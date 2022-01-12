# UniVIO: Unified Direct and Feature-based Underwater Stereo Visual-Inertial Odometry

Author: Miao

Year: 2021

Notes:
---
* new cmaera model for image rectification
* camera in a waterproof housing => refraction to be rectified
* New calibration method that separates lens distortion and water air refraction
* robust front-end for keypoint tracking
* sparse optimization model that integrates both photometric and reprojection errors
* Underwater dataset

Preprocessing:
* IMU pre integration on manifold (classic)
* takes refraction into account in camera calibration 

Data association:
* local optical flow tracking
* corners detected first, then strong gradient point if not enought
* KF selection: number of long termed tracked features and avg moving distance of tracked features
* LKT often failed when environnement illumination changes => new tracking method based on both optical flow and illumination changes estimation

Windowed optimization:
* classical bundle adjustement for reprojection error
* direct residuals = difference between patches intensity around points
* direct and feature based residuals are unified in a common residuals
* classi marginalization