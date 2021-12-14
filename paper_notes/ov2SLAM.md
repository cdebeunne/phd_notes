# OV2SLAM : A Fully Online and Versatile Visual SLAM for Real-Time Applications

Author: Ferrera & co

Year: 2021

Notes:
---
* efficient multi-threaded architecture (4 threads)
* when ORBSLAM is RT forced, accuracy decreases
* online bag of word for loop closing (first time in SLAM)
* PTAM first BA method in real time thx to parallelization
* limits triangulation by matching the most to existing points in the map
* CLAHE = contrast enhancement 
* pyramidal LKT for keypoint tracking
* RANSAC with 5 points to estimate the essential matrix with 3D points only
* initial guess with constant velocity assumption
* outlier rejection after reprojection error
* Keyframe creation based on parallax
* LKT for stereo matching
* retracking steps on the local map can be considered as small loop closures
* tracking on local map with 3D position of keypoints and BRIEF descriptors
* include in BA every KF that have at least 25 common observations
* 3D map points are parametrized with 2D pixel pose on the first KF and its inverse depth => one DOF per 3D point
* LC uses both keypoints from the SLAM and additionnal FAST features with BRIEF descriptors
* Pose graph optimization to take LC into account, then for each kp its new world pose is computed as $\lambda^{w^*} = {}^w T_{\alpha}^{new} {}^{\alpha}T_w^{old} \lambda^w$
* 200Hz SLAM by disabling LC and use of FAST features with a 50*50 pixel grid for KF creation

Commentaires:
---
Très bon papier avec plein de petites astuces à réutiliser pour mon projet