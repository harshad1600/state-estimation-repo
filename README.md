# __State estimation and localization for self-driving cars__

In this course, fundamental concepts in state estimation and localization for autonomous vehicles were covered. Many associated tools required in solving the state estimation problem were also taught.It started with least-squares technique which developed an insight regarding the problem of state estatimation and our approach towards it.Then, it moved on to various localization algorithms like Kalman filter,Extended Kalman filter and Unscented Kalman filter.Further modules were dedicated to formulation of sensor models for commonly used devices in autonomous driving such as Lidar,IMU,GNSS and wheel encoders.Finally a complete localization stack based on sensor fusion with EKF was developed in the final assignment which incorporated noisy recorded data from all sensors and estimated trajectory of the vehicle along with its uncertainty estimate.

## Extended Kalman Filter


Th extended Kalman filter is the non linear version of Kalman filter. A Kalman filter inherently exploits the properties of linear state space models with variables having Gaussian probability density function.

In case of localization of autonomous vehicles, it is required to make best possible use of all the noisy sensor data available.Kalman filter is one of the most popular choice when it comes to precise fusion of data from multiple sources. It works in two stages; the prediction step and the correction step. In prediction step, a motion model predicts the mean and covariance of random variables based on past estimate of the state and control inputs given.Then the sensor model evaluates the measurements to be expected based on our predicted state.In the correction step, the expected measurements are compared with actual measurements and then,the Kalman gain weighs accurately each of the above estimates depending upon their covariances and provides us with a more accurate guess of the current state with reduced uncertainty.

While dealing with non-linear models, they are first linearized with Taylor series approximation upto first order term and then processed by our basic Kalman filter algorithm.This modified version is nothing but our extended kalman filter.The workflow of extended kalman filter is represented below :


- Step 1:

	Prior estimate with non-linear motion model

	![](week2/images/equations/img_9.PNG)
- Step 2:

	Propogation of co-variance from past estimate

	![](week2/images/equations/img_10.PNG)

	![](week2/images/equations/img_11.PNG)

	The above Jacobians represent the gradient of motion model's function at our previous state.

- Step 3:

	Measurement model evaluates the observations to be expected given the prior estimate is true.

	![](week2/images/equations/img_12.PNG)

	![](week2/images/equations/img_14.PNG)

	The above Jacobians represent the gradient of sensor model's function at our prior estimate.

- Step 4:

	Computing Kalman Gain based on co-variances

	![](week2/images/equations/img_13.PNG)

- Step 5:
	
	Correction step

	![](week2/images/equations/img_15.PNG)

# Week 2 Assignment

In this assignment, the task was to precisely estimate the trajectory of an autonomous vehicle using available measurements and motion model.

Linear and angular velocities at each instant were provided.A differential drive motion model was formulated to predict the pose of the vehicle using this data.

![](week2/images/equations/img_5.PNG)

![](week2/images/equations/img_16.PNG)

The Lidar sensor measured range and bearing angle corresponding to each globally known landmark.The sensor model predicted the range and bearing measurements for these landmarks w.r.t. prior pose estimate.

![](week2/images/equations/img_6.PNG)

![](week2/images/equations/img_7.PNG)

Using the above formulations, the EKF algorithm was developed to fuse the available noisy data and provide with a much confident estimate of position of the vehicle.

## Result:

Ground-truth:

![](week2/images/gtruth.png)

Estimated trajectory:

![](week2/images/mygraph1.png)


