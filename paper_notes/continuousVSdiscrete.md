# Continuous-Time vs. Discrete-Time Vision-based SLAM: A Comparative Study

Author: Cioffi

Year: 2022

Notes:
---
* Better when sensors are not time-synchronized
* software provided of soa vision based SLAM in discrete and contiuous time
* continuous trajectory can be sampled at any time and remove the need to add an optimization variable at each measurement
* but you need to model a prior on the smoothness
* for continuous time methods, the time offset can be estimated on the fly

Related Work:
* B-spline, wavelet or gaussian process for continuous time traj
* for discrete SLAM, additionnal algorithm are needed to estimate the time offset between sensors

Method continuous:
* cumulative B-spline for the continuous time representation: $ x(t) = \sum_i B_i(t) x_{i,k} , x_i$ are the control points and $B_{i,k}$ are k order splines
* two B-spline for position vectors and rotation matrices in $SO(3)$
* initialization with K camera poses obtained with COLMAP, then an optimization is performed to get the continuous-time trajectory and another optimization is performed with GPS and IMU to get the gravity direction and the scale
* then full batch optimization if performed using MAP estimation with gaussian distribution for all measurements
* image feature measurements are obtained with COLMAP and optimized with reprojection error 
* accelerometer and gyroscope residuals
* classic GPS errors
* Cubic B splines for imu biases

Method discrete:
* IMU / camera offset obtained with VINS-Mono
* same initialization with COLMAP
* inertial residuals with pre integration
* classic batch optimization

Experiments:
* Ceres for the solver with autodiff
* I love this sentence: "How far is the local minimum from the global
minimum is unknown, and, in general, even the unknown
global optimum of the MAP estimation can be different from
the ground-truth due to modeling errors."
* optimal order of splines is 6 and optimal frequency for control points is 10 Hz
* experiments on sensor modalities: testing all combinations of 2 sensors => vision is the most important modality