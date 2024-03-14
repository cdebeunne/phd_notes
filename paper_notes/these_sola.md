# Towards visual localization, mapping and moving objects tracking by a mobile robot: a geometric and probabilistic approach

Author: Joan Solà <3

Notes:
---

### I - Kinematics
* Define euclidean vectors
* All frames are defined right handed
* good part on Euler angle and Quaternions
* Rotation matrix used to perform rotation of points, quaternion to store rotation in state vectors (easy for filtering derivation and differentation) and Euler angles for human interface

### II - Vision

* Lens are here to enhance the luminosity (awesome figure 2.1)

###  VIII - SLAM + MOT

* Observability analysis of the pb with bearing only sensor: the observer should move quite randomly, with faster dynamics than those of the target (complicated condition to meet)
* BiCAM slam (with static lmks) + 1 EKF per target
* objects considered punctual defined by their position and linear velocities