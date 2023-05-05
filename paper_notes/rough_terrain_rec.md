# Rough Terrain Reconstruction for Rover Motion Planning

Author: Gingras

Year: 2010

Notes:
---

* 2 steps : 
    * Surface generation from 3D LiDAR scan
    * Analysis to generate a compressed, navigable, triangular mesh
* deployed during Avatar Explore Space mission
* Delaunay 2D algorithm in polar coordinates *i.e.* on the 2.5d image on $(\theta, \phi)$ produced by the scan
* Survey on mesh generation: *MESH GENERATION AND OPTIMAL TRIANGULATION*
* Steiner Points = new vertices 
* Mesh simplification needed due to the big number of cells using 3D LiDARs
* Review of meshing technique for 3D PC: *survey of free-form object
representation and recognition techniques*

## Surface reconstruction
* undesired triangles:
    * triangles due to shadow regions
    * frontiers triangles (oversized triangles due to hills for example)
* Triple filter to remove meshes: 
    * threshold between the distance of the closest and farthest vertex to the sensor origin
    * threshold on triangle perimeter (for frontier triangle)
    * threshold on angle of incidence of the triangle
* Then apply the QSlim algorithm to simplify the mesh

##  Navigability
* Remove cells with a slope over a thresh w.r.t. the horizontal plane 
* Linear interpolation to correct the density of the mesh: compute an elevation grid by linear interpolation on the current mesh and perform again 2D Delaunnay triangulation on the sampled points. A simple thresholding on edge lenth remove edges that fills holes
* To enable path planning algorithms doing the point robot assumption, the obstacles are expanded by the largest dimension of the robot
* A Laplacian smoothing filter is also applied

## Experiments
* use a threshold of 25° for the slope
* Use a triangle quality metric $q=\frac{4 \sqrt{3} a}{h_1^2+h_2^2+h_3^2}$, that is 1 if the triangle is equilateral
* 20 seconds to generate a terrain model