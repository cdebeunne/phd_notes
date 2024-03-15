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
* Homogeneous matrix = transformation matrix
* defines distortion as an application $d : \mathbb{R}^2  \rightarrow \mathbb{R}^2 $
* defines image as an application $I : \mathbb{R}^2 \rightarrow \mathbb{R}_+$
* projection is the combination of the following $\mathbf{u} = pixellize(distort(project(ToFrame(\mathbf{p}))))$
* back projection: pixel unmapping, undistortion and back projection
* solution to invert distortion model: calibrate both distortion and correction model as polynomials
* compute the correction model from the distortion coefficients by solving a least square on a set of pairs $r_i, d_{di}$ 
* $\mathbf{p} = backProject(correct(unpixellize(\mathbf{u})))$

###  VIII - SLAM + MOT

* Observability analysis of the pb with bearing only sensor: the observer should move quite randomly, with faster dynamics than those of the target (complicated condition to meet)
* BiCAM slam (with static lmks) + 1 EKF per target
* objects considered punctual defined by their position and linear velocities