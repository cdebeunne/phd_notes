# SmartCaveDrone: 3D Cave Mapping Using UAVs as Robotic Co-Archaeologists

Author: Zhang

Year: 2017

Notes:
---
* metric and semantic maps with RGBD data on drones
* human/drone interraction
* off board parallel computing for 3D mapping and path planning 
* importance of light => cooperative lighting ie other drone to enlight the area
* RGBD have limited FOV
* KinectFusion = RGBD SLAM based on ICP and volumetric map
* ElasticFusion based on deformation graph
* But both fail with image blur or hard motion
* Work on bootstrap KinectFusion with IMU to gain robustness to rapid motion
* SFM solution for 3D reconstruction
* 3D mapping: segmanting and labelling object from the 3D pc here with supervised learning method on pc or 2D images
* Active SLAM: SLAM + taking decision on where to go next
* Active SLAM ok in 2D, much harder in 3D => require offline computing
* Sense and avoid with multiple RGB-D sensors