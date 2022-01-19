# Lidar-IMU-Based Ground Mobile Robot State Estimation with Mult-Submaps

Author: Zhai

Year: Into reviewing process for RAL

Notes:
---
* Tackle the problem of undulating ground
* Create submaps with KF and normal frames assuming constant ground for each submaps

Intro:
* There are a few features that can provide vertical constraints
* SE(2)-SE(3) method to compute relative transform (?) 
* redundancy between contributions 

Related Work:
* loosely-coupled fusion: IMU used to de skew the cloud and initialize optim
* tight fusion: coupling IMU deltas with LiDAR data 

Framework:
* A-l3. space between B and respresents
* A- $\mathbb{R}$ are missing 
* IMU is used for both de skewing and add factors
* Use a unified notation for Lidar 
* Classic roughness computation to classify edge and plane points
* rigid body assumption => change of XY plane -> change of ground 
* If the ground normal has changed according to a threshold, the ground has changed => KF
* LiDAR odometer based on edge and plane point matching 
* Because each normal frame of a submap lie on the same plane of the KF, the transformation is parametrized as a SE(2) pose
* To take into account 6DoF motion, SE(2) pose is converted to SE(3) pose and gaussian noise is added to the 3 other dimensions 
* LiDAR odometer factor is obtained by simply comuputing the transformation between current KF and previous submap
* Sliding window optimises both normal and KF
* C-3) a reference is missing 

Results:
* No information about run time in the experiment section

Commentaires:
* Skeptical about a loop closure factor inside a sliding window, this is supposed to work on the entire trajectory 
* Unifying Lidar notation
* The contribution is pretty clear but seems a bit limited for a letter submission 