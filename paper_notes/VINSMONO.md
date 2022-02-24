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
* KF selection based on parallax and on the number of tracked features
* classic IMU pre integration with bias correction

Initialization:
* aligning IMU pre integration with vision only structure
* Sfm on more than 30 tracked features on a sliding window with arbitrary scale:
-> pose of the first and last frame estimated with 5 pt alg

-> triangulation and PnP alg to estimate the pose of each frame

-> full bundle adjustement on the sliding window
* calibration of gyro bias, then gravity and metric scale with linear least square pbs

Tightly coupled VIO:
* visual inertial bundle adjustement formulation
* define the camera measurement residual on a unit sphere
* the two rays are substracted and the resultant vector is projected on a tangent plane
* at each new KF the latest KF and its meas are marginalized with the Schur Complement

Relocalization:
TODO