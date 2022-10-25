# Present and Future of SLAM in Extreme Underground Environments

Year: 2022

Author: Luca Carlone

Notes:
---
* Discuss results of the six teams at SubT
* aim: detecting and reporting artifacts with less than 5m precision in a unknown cave environement up to kilometers in less than an hour (with a team of robots and a single human operator)
* No light => visual failure, Fog and Dust => LiDAR failure, long corridor => LiDAR failure, self similar scenes => LC false positive
* emphasis is made on multimodal, LiDAR centric solutions
* *Kimera multi* distributed Kimera for multi robot operation
* SLAM Front end: registering salient features or dense scan for LiDARs

### Back end

* fusing front-end representations: all teams performed factor graph optimization
* *Bluepose graph optimization* is an instance of factor graph with only relative pose meas
* Tightly coupled: fusing directly sensor measurement, loosely coupled: fusing intermediate meas (like relative poses)

### Multi robot
* centralized arch: a base station collects data from all robots
* decentralized arch: each robot is treated as a base station
* distributed arch: each robot only exchange partial info from other robots and estimate its own map

## Team CERBERUS (Winner)

* onboard odometry and mapping with *CompSLAM*: loosely coupled fusion of sensor specific pose estimators
* coarse to fine fusion of independent pose estimates from: visual, thermal, inertial, depth, kinematic sources => robust to degraded conditions that will affect only a subset of sensors
* depth data from LiDAR used to improve depth estimaytes from visual and thermal imagery
* LOAM for lidar odom upgraded with a factor graph based fixed lag smoothing of 3 seconds using IMU measurements 
* centralized mapping server that uses LiDAR, Vision, IMU, wheel encoders into a single factor graph optimization (M3RM)
* each robot has a local M3RM node onboard to build a submap using odometry factors from the SLAM
* The M3RM base station create a global multi robot map using submaps
* Use DRACO compressing for LIDAR scans to reduce bandwidth
* Dirty details: a lot of parameter tuning, manually tuned visual and LiDAR covariances, no LC detection onboard => some submaps may accumulate drift and have to be manually removed from the multi robot map

## Team CoSTAR 

* LAMP SLAM: local front end for each robot, base station runs a front end for lc detection and a back end for global mapping
* LOCUS = Lidar centirc odometry estimator using multiple onboard lidars, point to plane ICP initialized using IMU or other odometry 
* LC detected simply using candidates that lies in a certain euclidean distance
* erroneous lc detected with Incremental Consistency Maximization (ICM) and Graduated Non-Convexity (GNC) which is used in a LM solver to perform outlier robust pose graph optimization
* The team curated 12 SLAM dataset for evaluation and benchmarking to obtain the best set of parameters

## Team CSIRO

* IMU + VLP16 mounted at 45° off horizontal: enabled 120° vertical FoV and the use of surfel features
* Uses planar surfaces elements (surfels) as dense featres created by clustering of new lidar points
* LiDAR IMU odometry in a sliding window: surfels are matched using k nearest neighbours in a descriptor space made of surfel's position, normal vector and voxel size
* decentralized multi robot SLAM: each robot communnicate with the base server and produce it's own optimized map based on *frames* extracted from each robot odometry system, overlapping *frames* are discarded to reduce complexity 
* hardware robustness (rarely discussed in SLAM)

## Team CTU-CRAS-Norlab
* Simple LiDAR IMU odometry on ugv
* Kalman filtering for IMU LiDAR on UAV, no deskewing on the scan to save time, intensity threshold to discard points due to dust or smog, LiDAR scans treated by A-LOAM (before filtering)
* totally decentrallized approach, multi robot map is available by concatenating each local map and using relative pose of each robot at take off
* No loop closure, no pose graph optimization

## Team Explorer
* Super Odometry: IMU centric odometry with three "sub factor graph" LiDAR-IMU, VIO, Thermal-IMU that are fused in a coarse to fine manner
* Radius search based Loop closure detection with registration using keycloud from keyframes of the Super Odometry

## Team Marble
* Lio SAM for LiDAR IMU odometry with naive euclidean metric for LC 
* Multi robot mapping with octomap
* High accuracy IMU for consistent odometry => low euclidean threshold for lc

## Common themes
* LiDAR IMU centric SLAM
* PreProcessing LiDAR scans onboard
* Mostly loosely coupled approaches that increases robustness to hardware and software failures
* No distributed algorithm

## Maturity
* very low drift (0.5% of distance travelled)
* multi modality increases robustness
* Lidar pc deskewing and downsampling is essential
* importance of outlier rejection for LC

## Open challenges
* Resilient perception: localization failure when falling => state estimation under unexpected collisions, dynamic reconfiguration "Curse of parameter tuning"
* explore new sensors like RADAR
* scalling up multirobots to 100 robots (wtf) that needs distributed algorithms
* scalling down for low cost sensing 