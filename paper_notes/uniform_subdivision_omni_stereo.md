# Uniform Subdivision of Omnidirectional Camera Space for Efficient Spherical Stereo Matching

Author: Kang

Year: 2022

Notes:
---

* equirectangular rectification -> low performances for stereo matching due to severe distortion around the poles
* novel subdivision scheme with spherical geodesic grid: one to one mapping from 2D images to spherical coordinates
* Latitude / Longitude = equirectangular projection (using angles)
* cubeMap projection reduces distortion but cannot be used for stereo matching due to complex computation for referencing 
* geodesic grid: projection using a dome composed of planar triangles

### Equal-epiline Subdivision on Geodesic Grid

* uses a icosahedral geodesic polyhedron as a geodesic grid (20 faces, 30 edges, and 12 vertices)
* when $\pi$ and $\pi^{-1}$ are not defined mathematically, we need a look up table that is computationnally expensive