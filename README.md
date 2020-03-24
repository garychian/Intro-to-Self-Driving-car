# Intro-to-Self-Driving-car
## Kalman Filter
### 1. Initial Prediction 
First, start with an initial predition of our car's location and probability distribution that describes our uncertainty about that predition. 

### 2. Measurement Update
We then sense the world around the car. This is measurement update step, in which we gather more information about the car's surroundings and refine our location prediction. 

### 3. Prediction (or Time Update)
The next step is moving, we predict where the car will move, based on the knoledge we have about its velocity and current position. And we shift our probability distribution to reflect this movement. 

### 4. Reapt 
Then, finally, we've formed a new estimate for the position of the car! The Kalman Filter simply repeats the **sense and move (measurement and prediiction)** steps to localize the car as it's moving. 

### TAKEAWAY
The beauty of Kalman filters is that they combine somewhat inaccurate sensor measurements with somewhat inaccurate predictions of motion to get a filtered location estimate **that is better than any estimates that come from only sensor readings or only knowledge about movement**
