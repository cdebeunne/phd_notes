# Invariant Kalman Filtering for Visual Inertial SLAM

Author: Martin Brossard

Year: 2018

Notes:
---

* Applied recently discovered UKF on Lie Group (UKF-LG)
* Composite manifold $SE_{2+p}(3)$ with pose, velocity and lmks
* UKF spares the user from jacobians computation
* compare left and right multiplication: right is better