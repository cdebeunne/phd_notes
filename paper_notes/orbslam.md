# ORB-SLAM: A Versatile and Accurate Monocular SLAM System

Author: Mur-artal

Year: 2015

Notes:
---
* uses ORB features for tracking and relocalization
* covisibility graph to restrain the search to a local area
* loop closing with pose graph optimization
* relocalization robust to illumination changes...
* ORB can be extracted at less than 33ms per frame
* tracking, mapping and loop closing run in parallel
* tracking does first pose estimation with *motion only* BA or relocalization module, then matches with reprojection and then pose is refined
* local mapping perform *local BA* and try to recover lost features
* each points stores: 3D pose, the mean of all its viewing directions $n_i$, its ORB descriptor, $d_{min}, d_{max}$ at which the point can be observed 
* generous policy for creation, but more restrictive after to remove redundant or wrong features

map initialisation:
* first find matching ORB points 
* parallel computation of $E$ and $H$ with RANSAC
* model selection with heuristic
* then full BA is performed


tracking:
* orb feature extraction with a greedy method to ensure homogeneous points distribution
* from 1000 to 2000 points regarding the resolution
* guided search of keypoints based on constant velocity model, if it fails a wider window is set for searching 
* pose is optimized with found correspondences 
* then the local map is reprojected to find new correspondences by comparing with the descriptor of the neighbouring unmatched points
* KF voting policy based on viewing changes

local mapping:
* update of the covisibility graph
* a point must fulfill these conditions: the tracking must work in 25% of the frames where it is visible, it must be observed from at least 3 KF (after a while)
* local BA optimizes all KF and all landmark in the sliding window 
* remove redundant KF: those where 90% of points are observed in at least 3 other KF