# DTAM: Dense Tracking and Mapping in Real-Time

Author: Newcombe

Year: 2011

Notes:
---

* Dense 3D depth map for each Keyframe => textured surface with millions of vertices
* Energy term based on photometric minimisation
* 6Dof tracking of the camera via image alignment of the dense model
* to perform dense mapping, the idea is to project a point in the volume on each overlapping image of a KF and to optimize the relative poses of images and the depth
* works only for a small baseline
* regularise the cost function with a huber norm over the gradient to make it more convex
* complicated iterative minimization based on duality principle
* perform a rough estimate $\hat{T}_{wl}$ then the dense model is projected on a virtual image at $\hat{T}_{wl}$ and a dense alignment between this image and the current one is performed
* pixels with photometric error over a threshold are discarded 
* bootstrapped with a point based stereo method until a first KF is acquired
