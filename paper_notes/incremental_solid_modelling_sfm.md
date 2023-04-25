# Incremental Solid Modeling from Sparse and Omnidirectional Structure-from-Motion Data

Author: Maxime Lhuillier

Notes:
---

* 2 Manifold surface reconstruction using a sparse pc from sfm algorithm
* advantages of sparse surface rec: quality of 3D points, low computationnal cost
* manifold = list of 3D triangle so that every the neighbourhood of every surface point is locally a disk
* the 3D delaunnay triangulation of a set of 3D point P is such that: each tetrahedra is on the convex hull of P, its vertex set is P, the circumscribing sphere of every tetrahedron does not contain any vertex.
* the genus of the surface is always zero (i.e. it has no hole)
* define a general test to see if a surface is manifold: if for every vertex, all the triangles that has this vertex can be ordered in a chain that link every triangle pair with an edge (i.e. the graph of v opposite edges must be a cycle)
* it also defines a substraction test and an addition test
* The length of the ray is bounded: the point uncertainty increases with the square of the length
* The size of the triangles is bounded (formally, the circumscribing sphere of each tetrathedron has a diameter bounded by a thresh)
* A rigorous sculpting method to add new point in the mesh so that it remains "Manifold" 

@inproceedings{Litvinov2013IncrementalSM,
  title={Incremental Solid Modeling from Sparse and Omnidirectional Structure-from-Motion Data},
  author={Vadim Litvinov and Maxime Lhuillier},
  booktitle={British Machine Vision Conference},
  year={2013}
}