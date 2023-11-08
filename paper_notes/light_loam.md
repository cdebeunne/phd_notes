# Light-LOAM: A Lightweight LiDAR Odometry and Mapping based on Graph-Matching

Author: Yi

Year: 2023

Notes:
---
* LiDAR SLAM for computation limited platforms
* Select non-conspicuous (non-visibles) features, then two stage matching (KD-tree + graph matching) that gives weight for odometry optim
* two streams for scan registration:
    * ICP
    * feature extraction (LOAM)
* Remove disjoint points, i.e. points at the borders that may represent outliers 
* Then compute the smoothness score to extract corners and planes
* divise each laser beam into 6 subregions and select weak corners and planes in each subregions as optimized features
* KD tree matching may lead to multi to one coresp case
* geometric consistency: the euclidean distance between targeted points remains constant through scans
* build a compatibility graph based on each hypothetical association and remove edges based on geo const 
* point to line residual and point to plane residual weighted by association scores from the graph matching
* mapping with two stage associations + ptl and ptp optim
* experiments on KITTI and on a 32 beam lidar embedded on a quadrotor