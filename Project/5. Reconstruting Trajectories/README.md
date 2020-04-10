# Reconstructing Trajectories
This project will real raw collection data from sensors in CSV format. 

## Main ideas about this project
Create a algorithm to visualize the CSV format input data.

The input data format will look like this:

as you can see, each entry in `data_list` contains four fields. Those fields correspond to `timestamp` (seconds), `displacement` (meters), `yaw_rate` (rads / sec), and `acceleration` (m/s/s).

**`timestamp`** - Timestamps are all measured in seconds. The time between successive timestamps ($\Delta t$) will always be the same *within* a trajectory's data set (but not *between* data sets).

**`displacement`** - Displacement data from the odometer is in meters and gives the **total** distance traveled up to this point.

**`yaw_rate`** - Yaw rate is measured in radians per second with the convention that positive yaw corresponds to *counter-clockwise* rotation. 

**`acceleration`** - Acceleration is measured in $\frac{m/s}{s}$ and is always **in the direction of motion of the vehicle** (forward). 

| timestamp | displacement  | yaw_rate | acceleration |
| :-------: | :----------: | :------: | :----------: |
| 0.0 | 0 | 0.0 | 0.0 |
| 0.25 | 0.0 | 0.0 | 19.6 |
| 0.5 | 1.225 | 0.0 | 19.6 |
| 0.75 | 3.675 | 0.0 | 19.6 |
| 1.0 | 7.35 | 0.0 | 19.6 |
| 1.25 | 12.25 | 0.0 | 0.0 |
| 1.5 | 17.15 | -2.82901631903 | 0.0 |
| 1.75 | 22.05 | -2.82901631903 | 0.0 |
| 2.0 | 26.95 | -2.82901631903 | 0.0 |
| 2.25 | 31.85 | -2.82901631903 | 0.0 |
| 2.5 | 36.75 | -2.82901631903 | 0.0 |
| 2.75 | 41.65 | -2.82901631903 | 0.0 |
| 3.0 | 46.55 | -2.82901631903 | 0.0 |
| 3.25 | 51.45 | -2.82901631903 | 0.0 |
| 3.5 | 56.35 | -2.82901631903 | 0.0 |

The output will look like this graph:

![](https://d17h27t6h515a5.cloudfront.net/topher/2017/December/5a3044ac_example-trajectory/example-trajectory.png)

## Code Details

### Funtions 

** `get_speeds`** converts the data_list to a list of speeds at given time stamps

```python
def get_speeds(data_list):
	speed = 0.0
    
    speeds = [speed]
    for index in range(1,len(data_list)):
        last_row = data_list[index-1]
        row = data_list[index]
        
        time = row[timestamp_index]-last_row[timestamp_index]
        acceleration = row[acceleration_index]
        speed += time*acceleration
        speeds.append(speed)
    
    return speeds

``` 
**`get_headings `** converts the data_list of headings by keeping track of the current heading and adjusting it by the `yaw_rate * time_delta`

returns the current heading at each time stamp in degree
```python
def get_headings(data_list):

	heading = 0.0
    headings = [heading]
    
    for index in range(1,len(data_list)):
        last_row = data_list[index-1]
        row = data_list[index]
    
        time = row[timestamp_index]-last_row[timestamp_index]
        diff = row[yaw_rate_index]
        heading += time*diff
        headings.append(heading)

    return headings
```
**`get_x_y`** Converts the data_list to a list of coordinates by keeping track of the
current position and adjusting it using the known heading, displacement and time delta.

returns list of vehicle coordinates

**`show_x_y`** Shows the vehicle's position and movement direction at all time stamps

```python
positions = get_x_y(data_list)
    headings = get_headings(data_list)
    
    X = [row[0] for row in positions]
    Y = [row[1] for row in positions]
    U = [cos(heading) for heading in headings]
    V = [sin(heading) for heading in headings]
    
    plt.figure()
    plt.title('Trajectory visualization')
    plt.axes().set_aspect('equal')
    Q = plt.quiver(X, Y, U, V, units='width')
    qk = plt.quiverkey(Q, 0.9, 0.9, 2, r'$2 \frac{m}{s}$', labelpos='E', coordinates='figure')
    plt.show()
    
    return
```

