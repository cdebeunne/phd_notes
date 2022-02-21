# Vision-Aided Inertial Navigation for Spacecraft Entry, Descent, and Landing

Author: Mourikis

Year: 2009

Notes:
---
* EKF that fuse visual features to IMU measurements for attitude, velocity and position in a rt fashion
* 0.16 m/s velocity error and 6.4m error for landing position
* 3D information of landmarks on the planet known from satellite images *mapped landmarks* (ML), rotationnal and rotationnal velocity with 2D-2D tracking *opportunistic features* (OF)
* experimentation during a sounding rocker entry test, system suited for FPGA hardware
* Classic Harris KP and crosscorellation for feature matching (no need for scale and rotation invariance for this scenario)
* OF only used for pose constraint between camera poses
* DIMES: descent and landing system of MER mission: feature tracking without IMU fusion

ML 3D-2D:
* ML enables global positionning, perform by matching templates between descent images and satellite images, but at a moment, these become hard to match and the system switches to OF tracking only
* For ML, map matching if performed: a harris pt is selected, with current pose a template of the point a Homoegraphy between the template and the map is computed. Then the convolution of the template is performed in the frequency domain (after FFT) to reduce comutationnal cost (convolution turns into a product)
* Match is marked if the correlation peak heigh and width passe a thresh

OF 2D-2D:
* high scale change in the end of the landing => LKT fails
* flat assumption of the scene => warping the initial image to successive images
* template warping given the homography, then 2D spatial coorelation based matching 
* matching very stable, no RANSAC needed

Estimator:
* state vector: $x_e = [q, p, v, b_a, b_g]$, N past poses of the camera (sliding window, N chosen as the maximum number of frames an OF can be tracked)
* Measurement model = reprojection errors based on absolute position (ML) or triangulated position (OF)
* petite subtilité pour les OF où il faut manipuler le résidu pour qu'il ne dépende pas de la détéction courante

Experiment:
* Rocket launch with GPS and 768*484 px camera
* 50  Hz IMU, 30Hz camera
* Offline implementation: 30Hz on a 2GHz CPU with N=20



