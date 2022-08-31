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
* attitude (roll and pitch) known from IMU
* for a line $\mathbf{l}$ visible on 3 views:
$$
l^1_i = \mathbf{l}^{2T} T_i \mathbf{l}^3 \ \ \  \text{for } i = 1,2,3
$$
* $T_i$ can be expressed only with columns of the projection matrices $P_i$ of the views
* Assuming calibrated images $P_i = 
\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0
\end{bmatrix}
\begin{bmatrix}
R_i & -R_i \mathbf{t}_i \\
0 & 1
\end{bmatrix}$ 
* And with known attitude $R_i = 
\begin{bmatrix}
C^i_y & 0 & S_y^i \\
0 & 1 & 0 \\
-S^i_y & 0 & C^i_y
\end{bmatrix}$
* We end up with 16 unknwon and each lines leads to 2 independant equations => 8 lines are enough to solve the pb
* degenerate case when line on two views are epipolar lines: the line L in 3D space is not defined => extremely unlikely with 3 views

Experiments:
* Usually 13 lines method (without known attitudes) for trifocal tensor or 7, 5 and 3 pts methods for 2 views estimation
* Faster in run time than 13 lines
* Experiments on KITTI using solvers in RANSAC fashion and concatenating pose measurements without refinement 