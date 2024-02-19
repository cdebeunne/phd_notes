# Voxblox: Incremental 3D Euclidean Signed Distance Fields for On-Board MAV Planning

Author: Helen Oleynikova

Year: 2017

Notes:
---

* Build ESDF (Euclidean signed distance field) from TSDF in a dynamically growing map
* ESDF = each voxel contains its euclidean distance to the nearest obstacle
* TSDF is the projective distance ie on the sensor ray
* Assume pose and point cloud available 
* For TSDF: add a weight to every point that ends up in a voxel that is based on $\theta$ the angle between the ray and the normal of the surface
* proposed a new weighting strategy for TSDF
* For merging: projection mapping (project a voxel to get its depth) or raycasting (update all the voxels met by the ray)
* proposed grouped ray casting: group all the pixels that projects on the same voxel and then perform raycasting on the mean of all pixels
* Truncation distance = distance below which measurement is ignored 
* proposed an algorithm to update ESDF with TSDF
* Error introduced by the fact of approximating the Euclidean distance by the projective distance