# Fusing Monocular Information in Multicamera SLAM

Author: Joan Solà

Year: 2008

Notes:
---

* each camera used as a mono sensor and all info is fused in a SLAM filter => desynchronisation of cam possible, self calibration, cooperative SLAM
* mono cameras = BO (bearing only) sensor
* difference between Sfm and SLAM: Sfm is solved offline with BA and SLAM is online 
* Sfm minimize error in measurement space, SLAM in state space
* stereo: limited 3D range, mechanical constraint, measurement space (u,v,d) disparity->0 for a point at infinity
* advanced VO: hardware based image processing, planar homographies (?), tightly coupled BA
* fusion of laser + camera: data association pb
*  here two sensors of same kind: appearance based matching possible

3D estimability:
* conic shaped pdf for the landmark position
* a landmark depth is estimated if the region of intersection of the rays is *closed* and *small*
* depth recovery impossible in the center when moving forward
* when moving laterrally the best estimable region is located in the center
* core algo = EKF SLAM based on inverse depth, each lmk represented by 
$$
i = [x_0, \theta, \psi, \rho]
$$
$\rho$ is the inverse depth of the euclidean distance to $x_0$, the angles are in global frame and $x_0$ is the position of the camera at init time
* as cameras are angular sensors vision measurements are more sensitive to camera rotation than translation

Multicamera:
* self calibration by including the relative orientation of the second camera in the EKF
* cooperative cameras: a master detect and initialize landmarks and a slave reobserves the map built by the master

Perception:
* Use active search (=searching features with prior info) as image processing framework
* strong Harris kp are selected and a 15*15 patch around it as a descriptor
* d>0 => positive depth, d<0 => negative depth
* distribution of inverse depth can be projected on the image => elliptic region in gaussian case
* prior: infinite depth ie inverse depth
* Affine patch warping for correlation matching to predict the best current landmark appearance

Experiments:
* self calibration: estimation of euler angles between cameras -> converge to correct result
* outdoor experiment for colaborative SLAM