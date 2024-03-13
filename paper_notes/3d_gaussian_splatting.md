# 3D Gaussian Splatting for Real-Time Radiance Field Rendering

Author: Kerbl

Year: 2024

Notes:
---

* represents a scen with 3D gaussians
* Init the process with camera poses and points from SfM
* (1-5 Millions of Gaussians per scene)
* Traditionnal method = reproject and blend Multiview stereo (MVS) from geometry
* starts with COLMAP, creates a set of 3D gaussians with the pc (mean, covariance and opacity $\alpha$), colors are represented with spherical harmonics (SH) (anisotropic color representation)
* project 3D gaussians in 2D for rendering 
* to keep properties of 3D covariances (spd) parametrize them as an ellipsoid (scaling vector s + rotation matrix)
* optimize both gaussians ($p, \Sigma, \alpha, SH$) and the guassian density (adaptive control of gaussian density)
* optimization based on both rendering and comparing
* the first gaussian from Sfm has uniform colors
* remove transparent gaussian (with $\alpha$ below a thresh)
* heuristics to handle the density of gaussians
* differentiable tile based rasterizer
* Memory consumption higher than NerFs (~20Go st)