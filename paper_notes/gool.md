# Get Out of My Lab: Large-scale, Real-Time Visual-Inertial Localization

Author: Torsten Sattler

Year: 2015

Notes:
---
* large-scale, real-time pose estimation on a mobile device
* map and  descriptor compression and efficient search algorithm
* Many solution relies on a server for real-time application *Scalable 6-DOF Localization on Mobile
Devices*
* Discarding measurements instead of marginalizing lead to suboptimal performance
* rt EKF based visual-inertial pose estimator with better performances than sliding window BA

System:
* Offline stage to compute a 3D point cloud of the scene with a SfM algorithm
* KF based VI SLAM track the movement and visual features are matched with the 3D pc
* Pose estimation with RANSAC and 2D-3D matches
* Use efficient binary descriptors FREAK that are projected to a real valued space (?) => reduces to 10 dimensions the descriptor, speed up the Knn search

Global 3D model:
* Big BA system with loop closure, IMU fusion for scale
* Compression: greedy algo to remove lmks, remove redundant KF, return a 3D pc of lmdks with covisibility information and descriptors
* Descriptor compression via *product quantization* 

Localization:
* RANSAC run time increase exponentilly with outlier ratio => covisibility filtering (only matches whose landmarks form clusters in the covisibility graph are kept)
* Pose recovery with PnP on inliers
* On the fly marginalization inspired by *Vision-aided inertial
navigation for spacecraft entry, descent, and landing.*
* EKF residual is computed by building the Jacobian H on the whole map, that is marginalized with QR decomposition only on matched landmark

Experiments:
* Map compression 136 MB -> 19 MB