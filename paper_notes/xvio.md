# Range-Visual-Inertial Odometry: Scale Observability Without Excitation

Author: Delaune

Year: 2021

Notes:
---
* Develop a VIO based on EKF with inertial for prediction, visual MSCKF update and range update for scale observability
* application on drone flying at constant velocity 
* range come from a 1D Laser Range Finder (LRF)
* range update is computed with 3 SLAM features, computed with 2D delaunay triangulation, that are assumed to form a planar surface
* perform observation analysis