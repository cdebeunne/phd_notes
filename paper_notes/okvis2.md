# OKVIS2: Realtime Scalable Visual-Inertial SLAM with Loop Closure

Author: Stefn Leutenegger

Year: 2022

Notes:
---

* Full VI SLAM based on the creation of a pose graph by marginalizing common observation
* BASALT, Kimera, VINS, ORBSLAM are *tightly coupled systems* = considering visual and inertial measurements with their internal states
* posegraph edges can be turned back into observation *reviving* old landmarks
* Semantic segmentation with CNN to remove dynamic objects
* OKVIS achieves computationnal tracktability with marginalisation
* factor graph optimization with ceres
* front end: matching, triangulation, seg CNN, place recognition
* realtime estimator: pose graph optimization frame only, sliding window, reviving old observation
* front end with BRISK kp matching
* Keyframe removed based on covisibility criterion
* Marginalization into relative pose factors (?)
