# Real-Time CPU-Based Large-Scale Three-Dimensional Mesh Reconstruction

Author: Piazza

Year: 2018

Notes:
---

## SOA:

* Meshing 3D = incremental algorithm from sparse keypoints
* extending soa incremental manifold mesh algorithm
* TSDF for large scale reconstruction *3D Modeling on the Go: Interactive 3D Reconstruction of Large-Scale Scenes on Mobile Devices*
* *Incremental solid modeling from sparse
and omnidirectional structure-from-motion data* only use points from SLAM when their 3D position is fixed
* Manifold Mesh = a mesh fully connected
* *Real-time mesh-based scene estimation for aerial inspection*: 3D meshing of the current viewpoint with a mono VIO for UAV, is not a manifold mesh

## Manifold Meshing
* weight for each tetrahedra that corresponds to the number of cameras that points a ray in the tetrahedra
* Update the mesh in a decreasing order 