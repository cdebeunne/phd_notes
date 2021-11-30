# Unsupervised Learning of Lidar Features for Use in a Probabilistic Trajectory Estimator

Author: Yoon, Barfoot & co

Year: 2021

Notes:
---
* feature and uncertainty learning with dnn for LiDAR odometry
* sparse structure of probabilistic formulation
* no groundtruth is required and network trained online
* does not need the estimator to be differentiable
* learning objective takes into account uncertainty
* approximate posterior as a multivarite gaussian distribution

Unsupervized DL for lidar odometry:
* optimisation over a w frames window
* apply EM (with E step optimizing on posterior and M step optimizing on parameters) for learning
* KPConv: convolution layer for point cloud based on sherical kernel
* The network compute descriptor, measurement covariance matrix and detection score for each point 
* Then a keypoint is computed for each voxel in a voxel grid using DNN output
* E step is basically factor graph optimization
* Hard thresholding on Mahalanobis distance for outlier rejection before M-Step
* Using covariance to evaluate the quality of a keypoint as well

Results:
* KITTI process LIDAR data to take distorsion into account
* Not running in real time because of KPConv layers