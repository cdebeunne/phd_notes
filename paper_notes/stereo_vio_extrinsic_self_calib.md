# Stereo Visual-Inertial Odometry With Online Initialization and Extrinsic Self-Calibration

Author: Yin

Year: 2023

Notes:
---

* During initialization: estimate mono VIO init with mono IMU calibration, then perform camera - camera calibration with mono VI BA
* The backend solver continuously refines extrinsic
* Camera - IMU rotation is first derived by solving a system using estimates of frame to frame rotations with 8 point algorithm and gyroscope
* Then the gyro bias can be estimated
* Perform scale, bias, gravity and IMU-camera calibration by aligning mono SFM with IMU pre-integration
* The entire pb is then refined with mono VI BA
* Then the camera-camera calibration is performed using the projection of all the landmarks refined previously on the right camera and by minimizing a 3D-2D reprojection errors
* have a marginalization prior
* include the extrinsics in the reprojection error (easy with the inverse depth parameterization) and the reprojection error is the sum of the left cam and right cam error