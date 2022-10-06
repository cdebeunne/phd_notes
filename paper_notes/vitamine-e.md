# VITAMIN-E: VIsual Tracking And MappINg with Extremely Dense Feature Points

Author: Yokozuka

Year: 2019

Notes:
---
* Extremely dense tracking of KP, indiect method
* Tracking using local extrema instead of KP
* novel optimisation technique: subspace GN newton to handle large number of kp
* generate and merge mesh for entire 3D model
* real time using only CPU

## Dense Tracking

* KLT may result with wrong correspondences over multiple views 
* Track all detected curvature local maxima:
$$
\kappa = f_y^2 f_{xx} - 2 f_x f_y f_{xy} + f_x^2f_{yy}
$$
* Coarse feature matching using BRIEF on low resolution image to init dominant flow estimation
* Affine transformation model using GN and M-estimation for dominant flow estimation ($x_i$ and $y_i$ is a feature correspondence)
$$
E = \sum_i^N \rho (||y_i - (A x_i + b)||_2)
$$
* Curvature extrema tracking using the prediction $\bar{x}_{t1}$ of the dominant flow and maximizing an evaluation function 
$$
F(x_{t1}) = \kappa(x_{t1}, t1) + \lambda w ( ||x_{t1} - \bar{x}_{t1}||_2)
$$

## BA
* Applying GN method to the BA objective function:
$$
H \delta x = -g
$$
* With $ H = \begin{bmatrix} H_{cc} H_{cp} \\ H_{pc} H_{pp} \end{bmatrix}$
diagonal blocks are sparse while $H_{cp}$ is dense
* For a high number of KP the H matrix becomes too large
* so the variable are partially updated using GN subspace (update variables using matrix blocks instead of handling the whole matrix)

## Dense reconstruction
* project 3D points onto the image and apply Delaunay triangulation, then propose NLTGV minimization as in *FLAME* to get smooth meshes
* Mesh integration with TSDF (?)

## CCL
* Only tested on EUROC
* RT on CPU (36 ms / frame)
