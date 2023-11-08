# FLaME: Fast Lightweight Mesh Estimation using Variational Smoothing on Delaunay Graphs

Author: Greene

Year: 2017

Notes:
---

* Pose the problem as a non-local variationnal optimization over a time varying Delaunnay graph of the scene geometry
* Focus on lightweight platforms (230 Hz on a single CPU core)
* Decouple mesh generation and VO
* strange notation for projection function
$$
\pi(x, y, z) =  (x/z, y/z) \\
u = \pi(K T_w^k p_w)
$$
* Uses variationnal smoothing to estimate the inverse depth map as a function $\xi : \Omega \rightarrow \mathbb{R}_+$
* The idea is to minimize an energy function $E(\xi) = E_{smooth}(\xi) + \lambda E_{data}(\xi)$, this can be solved using proximal methods
* $E_{smooth}$ is a NLGTV energy function and $E_{data}$ is a simple $L_1$ cost 

* works like this:
    * sampled pixels depth estimation
    * mesh construction
    * smoothness cost definition
    * minimizing the smoothness cost
    * propagating the mesh

### Depth Estimation

* it works with an image flow of known pose
* select features over a grid and estimate inverse depth by matching a patch of pixels on the epipolar line 
* need more spatially regular features for meshing 

### Mesh construction

* Compute the 2D delaunay triangulation of projected pixels using fast methods of (Shewchuk 2002)
* Delaunnay triangulation is optimal: it maximizes the minimum angle for each triangle

### Non Local Second Order Variationnal Cost

* define the variationnal cost over a delaunay graph 
* Discretize both NLGTV and L_1 terms over the graph
* Minimize this cost using Chambolle and Pock method

### Experiments

* compared surface reconstruction with LSD disabling the tracking module and putting groundtruth data instead
* collision free motion plan with A* using an occupancy grid made of FLAME meshes on a MAV