# Intro-to-Self-Driving-car
## Kalman Filter
### 1.1 Initial Prediction 
First, start with an initial predition of our car's location and probability distribution that describes our uncertainty about that predition. 

### 1.2 Measurement Update
We then sense the world around the car. This is measurement update step, in which we gather more information about the car's surroundings and refine our location prediction. 
- Base on bayes rule, and do multiplication for **new mu and sig**

### 1.3 Motion Update (Prediction)
The next step is moving, we predict where the car will move, based on the knoledge we have about its velocity and current position. And we shift our probability distribution to reflect this movement. 
- Base on total probability, and do addtion for **new mu and sig**

### 1.4 Reapt 
Then, finally, we've formed a new estimate for the position of the car! The Kalman Filter simply repeats the **sense and move (measurement and prediction)** steps to localize the car as it's moving. 

### TAKEAWAY
The beauty of Kalman filters is that they combine somewhat inaccurate sensor measurements with somewhat inaccurate predictions of motion to get a filtered location estimate **that is better than any estimates that come from only sensor readings or only knowledge about movement**

### 2.1 What is state
Car's position and it's movement is called **state** of the car

  - Position: x
  - velocity: v
  - `state = [0,50]`
### 2.2 Motion Model
In order to *predict* the state of a car at a future point in time, you rely on a **motion model**
> Note: No motion model is perfect :bowtie:

### 2.3 State Variables
For a constant velocity model, `x` and `velocity` will suffice.

But for a constant acceleration model, you'll also need our acceleration: `acc`.

Here is a state includes acceleration.

```python
# initial variables
x = 0
velocity = 50
acc = -20

initial_state = [x,velocity,acc]

# predicted state after three seconds have elapsed
# this state has a new value for x, and a new value for velocity 
dt = 3

new_x = x + velocity*dt + 0.5*acc*dt**2
new_vel = velocity + acc*dt

predicted_state = [new_x, new_vel, acc] # predicted_state = [60, -10, -20]
```
> For state, we always choose **the smallest representation** (the smallest number of variables) that will work for our model.

### Two threads to representing and Predicting state
### 3.1 Object-Oriented Programming
On the programming side, we'll use something called **object-Oriented Programming** as a way to represent state in code. We'll use `variable` to represent state values and we'll create `functions` to change those values.
#### Object
Objects **hold a state**; they hold a group of variables/properties and functions
- Variables
  - `__init__`
     stands for initialize and this this function frees up memory and allows us to create a specific Car object.The initialization means      that a computer now has the space to remember what this car object can do and what state it is in at any given moment. 
   > Operator overloading: `__init__` is called when we create a new object and `__repr__` is called when we tell Python to print  the string representation of a specific object!
   
  - `self.state = [postion, velocity]`
  
  - world: 2D grid
- Functions (Methods)
Eg. for car class with upercase 'C'. The class allows us to write code like `car.Car()`
  
  - `move(self)`
  function uses a constant velocity model to move the car in the direction of its velocity, vx and vy **and it updates the state**
  - `turn_left(self)`
  
  function rotates the velocity values to the left 90 dedgrees, and it updates the state!
  
  ```python
  def turn_left(self):
     """ Turning left "rotates" the velocity values, so vy = -vx, and vx = vy.
         For example, if a car is going right at 1 world cell/sec this means 
         vy = 0, vx = 1, 
         and if it turns left, then it should be moving upwards on the world grid 
         at the same speed! 
         And up is vy = -1 and vx = 0
         """
        
     # Change the velocity
     velocity = self.state[1]

     predicted_velocity = [
         -velocity[1],
         velocity[0]
     ]
        
     # Update the state velocity
     self.state[1] = predicted_velocity
  ```
  - `display_world(self)`

### 3.2 Linear Algebra
On the mathmatical side we'll use `vectors` and `matrices` top keep track of state and change it.

#### State vector vs matrix
  - state vector: an 2x1 state vector that contains variables: x and v
  
  <img src = "https://github.com/garychian/Intro-to-Self-Driving-car/blob/master/Images/state%20vector.png" width = 100>
   
  - Matrix multiplication
  
  <img src = "https://github.com/garychian/Intro-to-Self-Driving-car/blob/master/Images/matrix%20mutiplication.png" width = 400>

These are just our equations for our **constant velocity motion model**. Matrix multiplication let us create new, predicted state vector in just one multiplication step! The 2x2 matrix is often called the **state transformation matrix**

### 3.3 Matrices and Transformation of State
1. Matrix_addition
```python
def  matrix_addition(matrixA, matrixB):
     matrixSum = []
     row = []
     for r in range(matrixA):
         new_row = []
         for c in range(matrixA[0]):
             row.append(matrixA[r][c] + matrixB[r][c])
         matrixSum.append(row)
      return matrixSum
# note: cannot write as matrix_addtion([1,2,3],[4,5,6])
```
2. Matrix_multiplication
```python
def get_row(matrix,row):
    return matrix[row]
def get_column(matrix,column_number):
    column = []
    for r in range(len(matrix)):
        column.append(matrix[r][column_number])
    return column
def dot_product(vector_one, vector_two):
    result = 0
    for i in range(len(vector_one)):
        result += vector_one[i] * vector_two[i]
    return result
def matrix_multiplication(matrixA, matrixB):
    m_rows = len(matrixA)
    p_columns = len(matrixB[0])
    result = []
    for r in range(m_rows):
        row_result = []
        rowsA = get_row(matrixA,r)
        for c in range(p_columns):
            colsB = get_column(matrixB, c)
            dotProduct = dot_product(rowsA, colsB)
            row_result.append(dotProduct)
        result.append(row_result)
    return result
```
3. Matrix_transpose
```python
def transpose(matrix):
    matrix_transpose = []
    for c in range(len(matrix)):
        new_row = []
        for r in range(len(matrix[0]):
            new_row.append(matrix[r][c])
        matrix_transpose.append(new_row)
return matrix_transpose
```
4. Inverse_matrix
5. Identity_matrix








