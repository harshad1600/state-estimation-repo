# __State estimation and localization for self-driving cars__

In this course, fundamental concepts in state estimation and localization for autonomous vehicles were covered. Many associated tools required in solving the state estimation problem were also taught.It started with least-squares technique which developed an insight regarding the problem of state estatimation and our approach towards it.Then, it moved on to various localization algorithms like Kalman filter,Extended Kalman filter and Unscented Kalman filter.Further modules were dedicated to formulation of sensor models for commonly used devices in autonomous driving such as Lidar,IMU,GNSS and wheel encoders.Finally a complete localization stack based on sensor fusion with EKF was developed in the final assignment which incorporated noisy recorded data from all sensors and estimated trajectory of the vehicle along with its uncertainty estimate.

**Week2 assignment**

Problem Statement:

In this assignment, the task was to precisely estimate the trajectory of an autonomous vehicle using available measurements and motion model.

* Linear and angular velocities at each instant were provided.A differential drive motion model was formulated to predict the pose of the vehicle using this data.

 <img src="https://latex.codecogs.com/svg.latex?\large&space;x_{k}&space;=&space;x_{k-1}&space;&plus;&space;T\begin{bmatrix}&space;cos\left&space;(&space;theta_{k-1}&space;\right&space;)&space;&&space;0&space;&&space;\\&space;sin\left&space;(&space;theta_{k-1}&space;\right&space;)&space;&&space;0&space;&&space;\\&space;0&space;&&space;1&space;&&space;\end{bmatrix}\left&space;(&space;\begin{bmatrix}&space;v_{k}\\&space;\omega_{k}&space;\end{bmatrix}&plus;w_{k}&space;\right&space;)" title="\large x_{k} = x_{k-1} + T\begin{bmatrix} cos\left ( theta_{k-1} \right ) & 0 & \\ sin\left ( theta_{k-1} \right ) & 0 & \\ 0 & 1 & \end{bmatrix}\left ( \begin{bmatrix} v_{k}\\ \omega_{k} \end{bmatrix}+w_{k} \right )" />

 <img src="https://latex.codecogs.com/svg.latex?\large&space;x_{k}&space;=&space;\begin{bmatrix}&space;x&space;&&space;y&space;&&space;\theta&space;\end{bmatrix}&space;^T&space;is\:&space;current\:&space;2D\:&space;pose\:&space;of\:&space;the\:&space;vehicle" title="\large x_{k} = \begin{bmatrix} x & y & \theta \end{bmatrix} ^T is\: current\: 2D\: pose\: of\: the\: vehicle" />

<img src="https://latex.codecogs.com/svg.latex?\large&space;v_{k}\:and\:\omega_{k}\:are\:linear\:and\:angular\:velocity\:measurements"title="\large v_{k}\:and\:\omega_{k}\:are\:linear\:and\:angular\:velocity\:measurements" />

<img src="https://latex.codecogs.com/svg.latex?\large&space;w_{k}\:is\:process\:noise\:having\:zero\:mean\:normal\\distribution\:and\:constant\:covariance\:Q" title="\large w_{k}\:is\:process\:noise\:having\:zero\:mean\:normal\\distribution\:and\:constant\:covariance\:Q" />

* The Lidar sensor measured range and bearing angle corresponding to each globally known landmark.The sensor model predicted the range and bearing measurements for landmarks with globally known position w.r.t. prior pose estimate.

<img src="https://latex.codecogs.com/svg.latex?\large&space;y_{k}&space;=&space;\begin{bmatrix}&space;\sqrt{\left&space;(x_{l}-x_{k}-dcos\left&space;(&space;\theta_{k}&space;\right&space;)\right)^{2}&space;&plus;\left(y_{l}-y_{k}-dsin\left&space;(&space;\theta_{k}&space;\right&space;)\right)^{2}}\\&space;atan2&space;\left(y_{l}-y_{k}-dsin\left&space;(&space;\theta_{k}&space;\right&space;),x_{l}-x_{k}-dcos\left&space;(&space;\theta_{k}&space;\right&space;)&space;\right&space;)-\theta_{k}&space;\end{bmatrix}" title="\large y_{k} = \begin{bmatrix} \sqrt{\left (x_{l}-x_{k}-dcos\left ( \theta_{k} \right )\right)^{2} +\left(y_{l}-y_{k}-dsin\left ( \theta_{k} \right )\right)^{2}}\\ atan2 \left(y_{l}-y_{k}-dsin\left ( \theta_{k} \right ),x_{l}-x_{k}-dcos\left ( \theta_{k} \right ) \right )-\theta_{k} \end{bmatrix}+n_{k}^{l}" />

<img src="https://latex.codecogs.com/svg.latex?\large&space;x_{l}\:and\:y_{l}\:are\:ground\:truth\:coordinates\:of\:landmark\:l"title="\large x_{l}\:and\:y_{l}\:are\:ground\:truth\:coordinates\:of\:landmark\:l" />

<img src="https://latex.codecogs.com/svg.latex?\large&space;x_{k}\:and\:y_{k}\:and\:\theta_{k}\:represent\:current\:pose\:of\:the\:vehicle" title="\large x_{k}\:and\:y_{k}\:and\:\theta_{k}\:represent\:current\:pose\:of\:the\:vehicle" />
		
* Based on above motion model and sensor model,an Extended Kalman filter evaluated the pose estimate along with associated covariance.

## Result:

Ground-truth:

![](week2/images/gtruth.png)

Estimated trajectory:

![](week2/images/mygraph1.png)


