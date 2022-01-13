# Cluster-Based Loop Closing Detection for Underwater SLAM in Feature-Poor Regions

Author: Negre

Year: 2021

Notes:
---
* Classical methods for loop closure fail in underwater environements
* Loop correction necessary to limit the drift
* idea: loop closure based on Keypoint clustering, (keypoint cluster can belong to several KF)
* when matches are concentrated in a small area of the image, registration is not precise
* No tracking stage in the SLAM system, it fails => use stereo odometer instead (egomotion taken from *Stereoscan: Dense 3d reconstruction in real-time*)
* KF decision based on image overlap
* Orb KP and clustering with DBSCAN, use stereo pairs to triangulate KP
* Signature used is HALOC and it is based on SIFT descriptor (more efficient than BOW) and stored in a database
* graph structure with both clusters centroids and odometry inputs (solved with g2o)
* Loop detection by both proximity and cluster signature comparison
* Uses the stereo 3D points of the cluster to perform a PnP Ransac 3D to 2D correspondence for every loop candidate, if there is enough inliers, a loop is validated (the number of inliers is used to make a weight in the graph)
* Feature matching can be performed on several clusters from several past KF
* Outperform odom only and ORB SLAM on underwater datasets with loops
* KF to many KF loop mechanism enables many loops that are not detected with classic methods

