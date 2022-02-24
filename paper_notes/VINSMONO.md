# VINS-Mono: A Robust and Versatile Monocular Visual-Inertial State Estimator

Author: Qin

Year: 2018

Notes:
---
* robust procedure for initialization
* IMU pre integration
* online loop detection module
* 4 DOF pose graph optimization (?)
* fusion of 3 previous works: initialization IMU/cam, mobile VI odometry, graph fusion and optimisiation for VI SLAM
* MSCKF : VIO with KF

Measurement pre processing:
* vision KTL sparse tracker 
* shi and tomasi corner features