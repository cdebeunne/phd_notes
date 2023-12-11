# Robust Stereo Visual Inertial Odometry for Fast Autonomous Flight

Author: Sun

Year: 2017

Notes:
---
* Multi-State Constraint Kalman Filter (MSKF) to reduce computationnal cost
* Demonstrates that stereo is more robust for a similar computatinonal cost w.r.t. moncular solution
* represents state with standard aditive error so that $\delta q = [\theta 1]^T$
* visual measurements with stereo observations
* project the residual on the null space of the jacobian wrt the lmk pose (classic)
* 4 unobservable DoF in Kalman Filter VIO (global position and yaw)
* explanations in *Observability-based Rules for Designing Consistent EKF SLAM Estimators*
* uses KLT w/ FAST keypoints for both temporal and stereo tracks: * Empirically, corner features with
depths greater than 1m can be reliably matched across the
stereo images using KLT tracking with a 20cm baseline stereo
configuration*
