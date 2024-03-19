# KISS-ICP: In Defense of Point-to-Point ICP – Simple, Accurate, and Robust Registration If Done the Right Way

Author: Vizzo

Year: 2023

Notes:
---
* odometry estimation based on point to point ICP, adaptive thresholding for matching, motion compensation based on constant velocity model and point cloud downsampling
* Requires very few parameter tuning
* No loop closure
* No Pose Graph Optimization
* 5 steps for current pose estimation and map update:
    * Motion prediction and deskewing
    * subsample current scan
    * Find point to point correspondence between localmap and PC
    * registration to find relative motion
    * update the local map with subsample cloud
* Deskewing: noting $\mathbf{p}_i^*$ the deskewed point and knowing the angular velocity $\omega_t$, linear velocity $v_t$ and the time delay $s_i$ between the point ts and the first point of the scan ts:
$$
\boldsymbol{p}_i^*=\operatorname{Exp}\left(s_i \boldsymbol{\omega}_t\right) \boldsymbol{p}_i+s_i \boldsymbol{v}_t,
$$
* Downsample is done by using a voxel grid and keeping one point per voxel
* Found adventageous to keep a point in the cloud as the coord of the voxel
* Performs frame to local map registration
* Compute a ICP threshold based on a 3 sigma bound computed on all the motions of the local map
* Perform ICP on the Voxel grid with a robust kernel on the cost function