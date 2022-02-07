# Keyframe-Based Visual-Inertial SLAM Using Nonlinear Optimization

Author: Leutenegger

Year: 2013

Notes:
---

* tight fusion of IMU and reprojection in a single cost function
* marginalization to maintain a *bounded sized optimization window*
* historically fusion is based on filtering
* nonlinear estimation is good to reduce suboptimality due to linearization
* IMU introduces temporal constraints 
* landmarks are represented in homogeneous coordinates $p = [u^T s]^T$
* perturbation on the tangent space of state space: normal vector space for position, speed and bias and axis-angle perturbation for quaternion 
* VOnly has 6DOF, visual inertial 4DOF as gravity vector fixes two
* standard reprojection error
* accelerometer bias is modeled as a biased random walk
* descriptors (BRISK) are extracted oriented along the gravity direction (thx to IMU)
* brute force matching for keypoints of the local map
* outlier rejection performed with a chi squarred test on image coordinates obtained with IMU prediction
* marginalization on landmarks that were visible on the marginalized KF but not on the current one
