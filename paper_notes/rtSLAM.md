# RT-SLAM: a generic and real-time visual SLAM implementation

Author: Solà

Year: 2012

Notes:
---

* open source c++ library focused on genericity, and high execution speed
* data structure: world, map, robot, sensors, observatins ~ WOLF
* EKF SLAM as back end with efficient indexing
* data manager ~ processor
* map manager: maintain the map at a reasonnable size, remove poor landmarks
* active search: constraint search area where landmark can be found
* one point RANSAC: modification of RANSAC that uses EKF to obtain a whole model with less points
* lmk parametrized with Anchored inverse depth $(x_0, ray_0, \rho)$ in the beginnning (7DOF) then switched to Euclidean paramtrization when the pose has converged
* Harris KP with ZNCC for matching, robust to viewpoint change by using its predicted appearance 
* test with constant velocity motion model and VIO

