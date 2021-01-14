# Localization 
## Overview:

### Localization:
```
Localization is the process of determining the position or the state of a robot with respect to the enviroment.
```

### Provided Dataset:
Data provided in the [data.pickle](Resources/data.pickle):

| Variable | Description|
|-----------|------------|
| **t** | timestamps for the measurements provided|
| **x_init** | initial x position of the bot|
| **y_init** | initial y position of the bot|
| **th_init** | initial &theta; of the bot|
| **v** | Odometry reading of the velocity|
| **v_var** | Variance in the odometry reading of the velocity|
| **om** | Odometry Reading of the angular velocity|
| **om_var** | Variance in the odometry reading of the angular velocity|
| **l** | Location of the landmarks [a b]. Where a is the x coordinate of the landmark and b is the y coordinate of the landmark|
| **d** | Distance between the center of the bot and the LiDAR sensor|
| **b** | Bearing measurement provided by the LiDAR sensor|
| **b_var** | Variance in the Bearing measurement of the LiDAR sensor|
| **r** | Range measurement provided by the LiDAR sensor|
| **r_var** | Variance in the Range measurement provided by the LiDAR sensor|


### Importing the data into the code:

```python
import pickle
import numpy

with open('./data.pickle', 'rb') as f:
    data = pickle.load(f)
```

## Extended Kalman Filter Algorithm:

Refer to [Bayes Filter](https://youtu.be/oUq0a8jHSQg) and [Kalman Filter Algorithm](https://youtu.be/o_HW6GnLqvg) if you are unfimiliar with Bayes Filter and Kalman Filter


> *Extended Kalman Filter* is a Recursive Bayes Filter used for estimating the state of a robot by obtaining linear appoximation of the non-linear system.

![basic ekf algorithm](https://i.ibb.co/QrNHh0Y/Screenshot-2021-01-14-at-10-03-43-AM.png)

___
### Steps in State Estimation using Extended Kalman Filter:

#### Step 1: State Prediction
State Prediction involves predicting the state of the robot using only odmetry commands given to the motors of the robot.

![motion_model](https://i.ibb.co/nsxkyY4/Screenshot-2021-01-02-at-6-13-38-PM.png)

The above equation is the motion model. This is used to predict the position of robot given the position (x, y, &theta;)<sup>T</sup> at time *t-1* and control commands (u,w)<sup>T</sup> given to the robot at time *t*.

(x<sup>'</sup>, y<sup>'</sup>, &theta;<sup>'</sup>)<sup>T</sup> is the predicted pose of the robot at time *t*. 




