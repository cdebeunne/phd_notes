# A Tightly Coupled Feature-based Visual-Inertial Odometry with Stereo Cameras

Author: Lei Yu

Year: 2022

Notes:
---
* tightly coupled in the backend and in the front end
* IMU aided feature descriptors
* fast feature tracking based on IMU
* feature based methods with descriptor matching are more frequently applied in engineering 
* ORB do not describe in plane (roll) and struggle with out of plane (pitch, yaw) rotations

IMU aided front end:
* IMU predict the camera pose by integratio of $a$ and $\omega$
* perspective deformation due to camera motion
* uses a perspective deformation of the image patch to build the descriptor 
* prediction of the pose of a corner in the next frame with IMU, then performe descriptor matching with all the kp in a radius of 10 around

Backend:
* First pose is refined with EPNP Ransac
* CERES with pre integration, 3D to 2D residuals and 2D to 2D residuals

Results:
* ~ 75 ms per iteration
* IMU aided descriptor better than BRIEF or ORB on the trajectory precision level
* better than VINS FUSION & co on every EUROC sequence 

Papier de grande qualité