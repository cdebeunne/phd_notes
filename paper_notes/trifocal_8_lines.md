# Trifocal Tensor and Relative Pose Estimation from 8 Lines and Known Vertical Direction

Author: Guan

Year: 2022

Notes:
---

* Novel pose estimation algorithm based on lines and knowing the vertical direction of images

Intro:
* Non calibrated case: 8 points necessary to estimate the fundamental matrix, calibrated case: essential matrix with 5 pts
* tree focal relative pose = estimating pose from three views
* no texture with only lines => two views relative pose cannot be computed (except assuming constraints like orthogonality & co) but with 13 lines treenocular relative pose can be computed
* Reducing the number of requested matches permits to limit the RANSAC iterations
* trifocal tensor = 3x3x3 tensor

Pose estimation from lines and known direction:
* degenerate case when line on two views are epipolar lines: the line L in 3D space is not defined => extremely unlikely with 3 views