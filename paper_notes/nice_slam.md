# NICE-SLAM: Neural Implicit Scalable Encoding for SLAM

Author: Zhu

Year: 2022

Notes:
---

* Neural implicit representation produced over smoothed methods and are not scalable
* Uses hierarchical scene representation and pre trained geometric priors for indoor reconstruction
* Uses RGBD input
* IMAP = first SLAM with neural implicit representation uses a single MLP to represent an entire scene -> cannot handle large scenes
* The core of nice SLAM is hierarchical grid based neural encoding -> allows local updates
* Stores latent code of local geometry and optimizes directly on them
* Hierarchical scene rps: Scene geometry represented by four feature grid(coarse, mid, level, color) => 4 rendering network
* a rendering network takes as input the viewing rays of the pixels queried and the feature grid, returns occupancy values
* From left to right: uses camera pose and feature grid to generate a rendered RGBD image
* From right to left: image + depth to get the camera pose
* Alternative optimization to train the network
* Feature grids = voxel grids
* For each pixel, trilinear interpolation is performed to get the associated feature
* Each rendering mlp decode grid features to occupancy values
* Then uses a differentiable renderer that takes color and occupancy as input and returns the depth and color for each pixel
* Mapping optim: Geometric and photometric loss are both L1 loss