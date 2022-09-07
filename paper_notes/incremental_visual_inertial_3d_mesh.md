# Incremental Visual-Inertial 3D Mesh Generation with Structural Regularities

Author: Antoni Rosinol

Year: 2019

Notes:
---
* Building 3D mesh from sparse 3D landmarks -> do not fit the real scene
* enforce structural regularities in a factor graph formulation
* One would like a map representation that is:  lightweight, describe the topology and couple state estimation and mapping 
* (W. N. Greene and N. Roy 2017) decouple mesh generation and state estimation

### Approach
* structural regularities are encoded as constraints for the 3D mesh as planes
* Do not perform 3D tetrahedralisation which is computationnally expensive, perform 2D delaunay triangulation of keypoints
* geometric filter that removes 2D triangles that do not rely on the same plane
* Maintain the mesh over the receiding horizon of a fixed lag smoothing algorithm
* 2D Delaunay triangulation is performed from scratch at each frame
* Merge local 3D mesh to the global one by ensuring that no duplicated 3D faces are present, marginalized landmarks lead to vertex removal in the mesh
* Detect vertical with mesh normal and ground plane with height histogram 

### Back end

* structureless approach for non structural landmarks (?)
* Variable to be estimated: state of the system, 3D landmarks on planes and planes
* 4 factor: 
    * structural regularity factor (landmark to plane)
    * IMU pre integration factor
    * constrained landmark factor (projection)
    * structureless landmark factor
* regularity constraint $r_R = \mathbf{n} . \mathbf{l} - d $ with $\mathbf{n}$ the normal of the plane and $d$ the distance to the world origin of the plane

### Experimentation

* Compared VIO with only structureless, structureless + projection and structureless + projection + regularity factors