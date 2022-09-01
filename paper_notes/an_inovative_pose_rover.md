# An Innovative Pose Determination Algorithm for Planetary Rover Onboard Visual Odometry

Author: Botian Zhou

Year: 2022

Notes:
---

* New pose determination algorithm for VO with an angle based criterion
* VO is based on 3D-2D point correspondence
* The aim is to minimize the angular error set as a cost function with a Huber Kernel, the angular distance is approximated by $\delta \theta = || d_i^c - p_i^c||^2$
* Initial estimation is computed by solving $[d_i^c]_{\times} (R p^w_i + t) = 0$ with QR factorization  
* An intermediate coordinate system is generated with the initial pose estimation, thus the alignement with the real camera coordinate can be approximated with Lie Algebra: the alignement is computed with QR factorization as well
* Finally GN optimization is used to refine the global pose with a single iteration
* real and simulated experiments 
* exp on KITTI with the 1500 first frames and bundle andjustment with SIFT features (wtf?)