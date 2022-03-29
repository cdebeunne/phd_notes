# Robust Estimation graph optimization Anymal

Author: David Width

Year: 2019

Notes:
---

* factor graph for legged robot
* IMU & Camera & Encoder
* Want to estimate a sliding window of robot state (pos, velocity, orientation of base) and a map
* angular position of articulation not estimated
* factors for lmk, factors for legged odometry
* Harris corner detection + KLT tracking 
* Outlier rejection: RANSAC with essential
* Use all frames as KF
* detect no Harris if not enough tracks
* add a landmark in the map if length of track longer than a 1s
* init with all the rays 