# A Benchmark Comparison of Monocular Visual-Inertial Odometry Algorithms for Flying Robots

Author: Scaramuzza

Year: 2018

Notes:
---

* Evaluates several mono VIO, on different hardware setups on the EUROC dataset
* OKVIS: first KF, optimization based system based on reprojection error
* ROVIO and MSCKF: two EKF systems
* SVO + MSF: loosely coupled VO and inertia in an EKF
* SVO + GTSAM: SVO + full smoothing backend of ISAM2
* SVO + GTSAM is the best on smooth trajectories but fail on tough one: poorly triangulated feat cuase numerical instabilities