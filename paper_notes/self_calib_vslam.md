# Self-Calibration and Visual SLAM with a Multi-Camera System on a Micro Aerial Vehicle

Author: Heng

Year: 2014

Notes:
---
* config: two stereo pairs facing opposite directions with IMU
* Self calib based on the generalized camera model (using many cameras as one)
* *Motion Estimation using Multiple Non-Overlapping Cameras for Small
Unmanned Aerial Vehicles* Kanade paper about non overlapping cams (without scale estimation)
* M. Tribou: thesis about PTAM version with non overlapping cam, doesn't scale to large environments
* Self Calib step:
	* Estimate a consistent map for each stereo system with VSLAM
	* Hand eye alignement to get a raw estimate of the inter stereo calib
	* Merge of the two maps
	* Perform full BA (intrinsics, extrinsics, poses and 3D points)
* Robust pose graph optimization for loop closure (with relative pose given by stereo VO and loop closures)
* Propose a pose estimation based on bearing vector and with gyro integration for rotation estimation 
