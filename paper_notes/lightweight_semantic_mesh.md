# Lightweight Semantic Mesh Mapping for Autonomous Vehicles

Author: Herb

Year: 2021

Notes:
---
* 3D semantic mesh by fusing VO, dense depth estimation with deep learning and semantic with deep learning
* Voxel and surfel based methods are computationnaly expensive and require a lot of storage (e.g. SurfelMeshing, *On fast surface
reconstruction methods for large and noisy point clouds*, *Real-time Scalable Dense Surfel Mapping*)
* Meshing based on sparse set of kp: *Incremental reconstruction of urban
environments by edge-points delaunay triangulation*, *Real-time CPU-based large-scale 3D mesh reconstruction*

Method:
---
* ORB-SLAM2 as VO system
* PSPNet for 2D semantic segmentation
* Perform Constrained Delaunay Triangulation + Delaunay Refinement
* Estimate the covariance of each vertex in the camera frame using 2D and depth uncertainties
* Need to perform probabilistic vertex matching 3D to 2D, as it is not using the local map of ORBSLAM2.
* An incremental mesh update is performed for each object:
    * Compute a 3D Mesh from the current active Mesh
    * Conflict detection (overlapping semantics)
    * Update probabilistic vertices using fast Covariance Intersection

Exp:
---
* Use GA-Net to predict depth from stereo or struct2depth to predict depth from monocular 
* Compare to TSDF reconstruction that is the semantic component of KIMERA
* Presents qualitative results on images and videos
* Evaluation metric: semantic chamfer distance with point cloud generated from mesh with a density of 2500 pts/m^2:
$$
e_{g \rightarrow \mathcal{R}}=\min _{r \in \mathcal{R}, c_g=c_r}\|r-g\| \quad e_{r \rightarrow \mathcal{G}}=\min _{g \in \mathcal{G}, c_r=c_g}\|g-r\| .
$$
* Evaluate on KITTI and their own dataset
* Fastest method
