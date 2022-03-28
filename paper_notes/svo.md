# SVO: Semi-Direct Visual Odometry for Monocular and Multi-Camera Systems

Author: Forster

Year: 2017

Notes:
---

* Semi-direct: track high intensity gradient pixels with direct methods and joint optimize with feature based methods
* introduce *sparse image alignement* algorithm (direct method for frame-to-frame motion)
* 3D features creation with Bayesian recursive depth estimation
* pose refinement with BA (BA used only for refinement)
* very fast: select features only on KF, direct method permits to get rid of data association, sparse reconstruction
* generalization of SVO to edgelet, wide fov and multi cam
* motion estimation thread: frame to frame algnement + image alignement with map + BA refinement
* mapping thread: at each KF, 3D point init if the uncertainty of the bayesian filter is low enough
* use scaramuzza model for fisheye 

Discussion:
* tracks less features than LSD SLAM, more efficient with high frame rate cameras
* high speed mode: refinement with only the latest pose
* high accuracy mode: smoothing with iSAM2