# __State estimation and localization for self-driving cars__

In this course, fundamental concepts in state estimation and localization for autonomous vehicles were covered. Many associated tools required in solving the state estimation problem were also taught.It started with least-squares technique which developed an insight regarding the problem of state estatimation and our approach towards it.Then, it moved on to various localization algorithms like Kalman filter,Extended Kalman filter and Unscented Kalman filter.Further modules were dedicated to formulation of sensor models for commonly used devices in autonomous driving such as Lidar,IMU,GNSS and wheel encoders.Finally a complete localization stack based on sensor fusion with EKF was developed in the final assignment which incorporated noisy recorded data from all sensors and estimated trajectory of the vehicle along with its uncertainty estimate.

<<img src="https://latex.codecogs.com/svg.latex?\large&space;v_{k}\:and\:\omega_{k}\:are\:linear\:and\:angular\:velocity\:measurements"title="\large v_{k}\:and\:\omega_{k}\:are\:linear\:and\:angular\:velocity\:measurements" />

## Result:

Ground-truth:

![](week2/images/gtruth.png)

Estimated trajectory:

![](week2/images/mygraph1.png)


