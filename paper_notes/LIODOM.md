# LiODOM: Adaptive Local Mapping for Robust LiDAR-Only Odometry

Authors: Emilio Garcia-Fidalgo, Joan P. Company-Corcoles, Francisco Bonnin-Pascual and Alberto Ortiz

Into review process

Notes:
---
* LiDAR only odometry based on point-to-line registering on a local map 
* Efficient data structure for map representation
* whole map can be represented as KD-tree but performances degrades with the number of pts ie do not scale well
* Here a hashing scheme is used to represent the map
* Highly inspired by LOAM, inside a factor graph

Related work:
* Loosely-coupled solution with IMU = de skewing point cloud or using IMU to build a prior
* Tightly-coupled: fuse data jointly (in a graph, in a filter..) eg. LIO SAM
* § 3, l9 : a* slinding window

System overview:
* sweep = whole point cloud made of several 2D scans
* odometry module extracts LOAM edges and plane and estimates the current pose with registration on a adaptive local map 
* mapping build the global and local map

LiDAR Odometry:
* two thread
* first thread: feature extraction with curvature score $c$ (the formula can be reminded)
* sectors division + non max suppression for edge points
* second thread: pose optimization
* point to line distance computed with the nearest neighbours of an edge point in the local map
* weight on point to line factor based on range of the lidar meas.
* Pas mal, assez clair

LiDAR Mapping:
* Maps of cells, that are cuboids of fixed sizes $M = \{ \mathbb{H}, \mathbb{C} \}$ $\mathbb{H}$ is the hash table and $\mathbb{C}$ is the set of cells
* Map of only edge points=> more sparse
* Local map built with the cells up to a certain range of the current robot pose, it is thus *adaptive*

