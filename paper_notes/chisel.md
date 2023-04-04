# CHISEL: Real Time Large Scale 3D Reconstruction Onboard a Mobile Device using Spatially-Hashed Signed Distance Fields

Author: Klingensmith

Year: 2015

Notes:
---

* rt dense 3D reconstruction
* use VIO for localization and TSDF for mapping
* IMU, Camera, depth sensor
* TSDF = alternative to occupancy grid, negative inside obstacles, positive outside obstacles
* A distance field is $\Phi: \mathbf{R}^3 \rightarrow \mathbf{R}$ that assigns the distance to the nearest surface to each 3D point, the zero isocontour contains the surface of the scene
* Truncated means that a threshold is set to the maximum distance
* The TSDF is built using each rays in a scan 
* Meshing is performed using Incremental Marching Cubes