# Smooth Mesh Estimation from Depth Data using Non-Smooth Convex Optimization

Author: toni Rosinol

Year: 2021

Notes:
---

* build a 3D mesh directly from depth map and 3D sparse landmarks
* non smooth convex optimization problem that runs on real time
* can be used with any VO pipeline 
* can represent piece wise planar surfaces with very few parameters while providing information about topology of the scene
* uses GPU :(
* same mathematical machinery as FLAME

### Related Work
* tetrahedral 3D meshes similar costs and benefits than volumetric approaches, leads to artifacts and are expensive
* 3D mesh directly from triangulation trade off quality and accuracy for speed (on ground robot *3D navi-
gation mesh generation for path planning in uneven terrain* & *ovpc mesh: 3d free-space representation for local
ground vehicle navigation*)
* VITAMIN-E: mesh with extremely dense sparse features
* non euclidean deep learning methods too slow and computationnaly expensive