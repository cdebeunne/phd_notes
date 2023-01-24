# Densifying Sparse VIO: a Mesh-based approach using Structural Regularities

Author: Toni Rosinol

Year: 2018

Front End:
---

*  Classical Harris detector, KLT tracker, RANSAC, Keyframe selector
* 3D mesh generator : 2D Mesh to 3D mesh with filtering faces that do not represent an actual surface
* Regularities detector: landmark to plane data association
* 2D triangulation prevent from doing a 3D tetrahedralisation that is computationnally expensive
* 3 pb : 
    * noisy positions of lmks
    * irregular density of the point cloud
    * point cloud is morphing, points are removed and added at each iteration
* Only keypoints that have a stereo corespondence and a 3D landmark are kept for mesh
* 3D Mesh update:
    * at each frame a 2D Mesh is created from scratch
    * check for every duplicate triangle wrt the last 2D and delete them from the current mesh
    * convert into 3D mesh and append it to the current 3D mesh
    * remove any rows with marginalized landmarks 
* Mesh filtering: 
    * pb of triangles from walls to ground and outliers
    * remove silver triangles (triangles with two very accute angles)
    * remove triangles with a large ratio between largest and smallest side
    * remove triangles with an edge larger than a thresh (?)
* Uses the mesh normals and elevation histogram to extract horizontal planes (table and ground)


