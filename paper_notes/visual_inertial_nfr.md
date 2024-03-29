# Visual-Inertial Mapping with Non-Linear Factor Recovery

Author: Cremers

Year: 2019

Notes:
---

* inertial meas contains a little information after a few second of integration
* hierarchical approach: recovers local VIO estimate, then non-linear factors are extracted after marginalization for full BA
* VIO layer: fast tracking kp, mapping layer: lighting and invariant k
* velocity and biases not estimated: pre integration is not used
* performs full BA 

VIO:

* pyramidal KLT patch tracker with FAST corners
* representation of bearing vectors with stereographic projection ie unit length bearing vector parametrized on a 2D plane
* IMU error with pre integrated delta with fixed biases 
* Classic marginalization that leads to a dense prior between all KF pose
* VIO pb: Consists of $m$ temporal states (with pose, velocity and IMU bias) and $n$ old keyframes states (only pose) + landmarks  

Mapping:

* implicit loop detection with ORB feature matching
* loop closure with reprojection error and factor recovered by NFR
* Here uses NFR to transfer information from VIO to map optimization
* optimizes all keypoints + all the factors from NFR
* topology: absolute factor on roll-pitch, yaw and absolute position + relative pose



