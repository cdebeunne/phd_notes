# 3D Modeling on the Go: Interactive 3D Reconstruction of Large-Scale Scenes on Mobile Devices

Author: Schöps

YEar: 2015

Notes:
---

* Uses a mono VIO using a fisheye with an EKF to estimate motion, then compute depth maps directly from fisheye images that are locally fused and filtered
* works in rt on a google Tango
* Volumetric data stored in voxels through the sum of truncated signed distance function (TSDF)
* use plane sweep stereo directly on fisheye images
* depth update via EKF again
* outliers: check consistency over time, variance thresholding, angle thresholding, connected components 