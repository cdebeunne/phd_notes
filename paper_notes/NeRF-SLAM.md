# NeRF-SLAM: Real-Time Dense Monocular SLAM with Neural Radiance Fields

Author: Toni Rosinol

Year: 2022

Notes:
---

* geometric and photometric 3D mapping pipeline 
* Monocular camera is the simplest sensor to calibrate
* great reference for deep learning based SLAM
* NeRF (neural radiance fields) enable geometrically accurate 3D representation
* Using depth supervision with NeRF may enable to prevent from "ghost" geometry
* Possibility of a monocular SLAM pipeline with dense depths map and uncertainty estimates to provide the right information for a NeRF of the scene
* DROID SLAM = uses state of the art dense optical flow method to perform VO (with a learned upsampling operator for dimensionnality)
* Real Time operation with dense SLAM and NeRF training running in parallel
* The tracking module computes a dense optical flow with a CNN and performs dense BA to obtain pose + depth and also computes covariances for both poses and points
* Training NeRF with a noisy depth map from SLAM -> biased reconstruction : uncertainty aware loss leverage this problem
* Depth L1 for mapping metric and peak signal-to-noise ratio (PSNR) between input RGB and rendered images
* Limitations: 11Gb of GPU memory