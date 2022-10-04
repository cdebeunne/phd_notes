# Dynam-SLAM: An Accurate, Robust Stereo Visual-Inertial SLAM Method in Dynamic Environments

Author: Yin

Year: 2022

Notes:
---
* VISLAM in dynamic envirronment: couple stereo scene flow with IMU for dynamic feature detection
* Tightly couples dynamic (virtual landmarks) and static features in non linear optimization (instead of discarding dynamic features)
* uncertainty estimation of the scene flow
* in soa: semantic segmentation or geometric methods to remove dynamic features (for vision only)
* dynamic feature detection is a thread running in parallel
* scene flow is a 3D vector field define for each point motion in the world frame (should be zero for static points)
* to obtain scene flow $\delta M $ between adjacent frames $i$ and $j$: use KLT for frame to frame matching and SGM (semi global matching) for disparity to estimate the lmk $n$ in cam frame $ \{ p^{c_i}_n, p^{c_j}_n \} $ and use IMU preintegration to get ${}^{c_i} T_{c_j}$
$$
\delta M_n = p^{c_i}_n - {}^{c_i} T_{c_j} p^{c_j}_n
$$
* histogramm analysis demonstrates that scene flow is corrupted by depth noise and other factor => thresholding doesn't work
* So compute the covariance of the scene flow taking into account: IMU pre integration, SGM disparity estimation, KLT tracking
* then uses $\chi^2$ rejection
* virtual landmark: use a constant motion model to predict its future pose
* Loop closure module using only static features
* better than ORBSLAM & co on dynamic env