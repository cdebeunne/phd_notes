# Stereo Orientation Prior for UAV Robust and Accurate Visual Odometry

Year: 2022

Author: Ran Duan

Notes:
---

* Observation: 2D-3D coresp with low reprojection error => high pose estimation error
* Idea: implicit pose error is better for outlier rejection, possible with stereo only
* Perform as well as IMU aided system
* Stereo view => prior knowledge of orientation
* Why visual pose estimation can produce large error? => bias in orientation of inliers
* It is still chalenging to develop a stereo VO solution
* Inlier/outlier polynomial system ? using the squared norm of error ?

Methodology:

* grid Feature Detection to offer a proper feature distribution
* Stereo intialization , KLT tracking and pnp for pose estimation
* Typical VO
* the pose of a landmark is evaluated by interpolating between the last estimation and the current one, and it is declared as an outlier with an SOS feasability test (?)
* Build an optimization problem based on the 2D-3D projection
$$
p_k = RP_k + t \\
R = (I-[c]_{\times} )^{-1}(I + [c]_{\times}) \\
(I-[c]_{\times} ) p_k \times \left ( (I + [c]_{\times})P_k + (I-[c]_{\times} )t \right) = 0
$$
* SOS theory ultra hard to understand :o
