# Surface Reconstruction from Multi-View Stereo of Large-Scale Outdoor Scenes

Author: Salman

Year: 2010

Notes:
---
* Dense 3D point cloud from multiview stereo, uses 2D delaunay triangulation
* according to *A
comparison and evaluation of multi-view stereo reconstruction
algorithms*, 4 class of methods:
    * working on a 3D volume
    * variationnal methods 
    * fusing multiple depth maps
    * extract 3D points and fit a surface
* A triangular depth map is made for each images, then triangles lifted in 3D. The triangle soup is refined by combining visibility and photo consistency constraints (?)
* The Voronoi cell $V(p_i)$ , associated to a point $p_i$ , is the region of points that are closer to $p_i$ than to all other sites in $P$
* Takes as input a set of calibrated images and a set of tracks 
* Several steps:
    * Merging close tracks 
    * Filters outliers by distance to nearest neighbours and low parallax
    * Smooth the surface by polynomial fitting of the neighbours of each point and reprojection
    * Detects contour by gaussian filter + canny, 2D triangulation over all tracks and 3D lifting
    * filter triangle soup
* Filter triangle soup:
    * visibility constraint: remove any triangle that is crossed by the ray of a 3D point
    * if the angle between the normal and the ray of its vertex is over 80°
    * big triangles that have normal shape have photoconsistency check *i.e* the triangle on every view should have a small NCC
* Reconstruction with *Provably good sampling and meshing of
surfaces* but it needs a prior