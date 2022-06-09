# BabelCalib: A Universal Approach to Calibrating Central Cameras

Author: Lochman

Year: 2021

Notes:
---

* Calibration toolbox for omni cameras
* Rough calculation of a back projection model first (pixels -> rays), then refine the camera model
* Corner correction step 
* The initial estimate is done with the Division model

Preliminaries:
* Micusik equation: for a scene point $X$ and an image point $u$ :
$$
\gamma g(A u) = P X
$$
* A : maps from image coord to sensor coord (with scale, center of image and pixel ratio)
* g : map from retinal plane to ray direction (non linear) $g(u) = g(u, v, \psi(r(u)) )$
* P : Camera matrix (K * T)
* Radial fundamental matrix: $0 = u^T F_r x$

Initial estimate:
* solving the radial fundamental matrix to recover the center of projection and the camera pose
* correction of corners with epipolar constraint and fundamental matrix refinement => proved to increase accuracy on simulated data
* solving intrinsics of division model of degree 4 (empirical value from simulated data)
* model to model regression to get initial estimate of the wanted camera model
