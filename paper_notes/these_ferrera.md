# Monocular Visual-Inertial-Pressure Fusion for Underwater Localization and 3D Mapping 

Author: Maxime Ferrera

Year: 2019

Notes:
---

Intro:

* Use of Remotely Operated Vehicles (ROV) in the context of underwater archeology
* Doppler Velocity Logs (DVL) estimation of the velocity based on frequency shift of acoustic beams
* Pressure sensor: estimation of depth from the water surface
* Acoustic Positionning Systems: replacement of GNSS system
* Dead-Reckoning (DR) =  using navigational sensors (IMU, compass, DVL) only
* Sonar based SLAM: can model lmk observation in EKF SLAM, graph SLAM or particle filter
* VAN framework with an Information Filter: keep past estimate and low complexity
* For vision based 3D reconstruction: pure sfm or EKF SLAM as a prior trajectory
* Monocular choice for practical reasons -> having sensor setup in a single housing 
* public underwater dataset: AQUALOC

Mathematics:
* P3P: the pose of the camera wrt to $w$ can be known with at least 3 known lmk
* Least Square:
    * for linear pb $L(\mathcal{X}) = || b - H \mathcal{X}||^2_{\Sigma}$ the closed form solution is given by $ \mathcal{X} = (H^T \Sigma^{-1} H)^{-1} H^T \Sigma ^ {-1} b$
    * for non linear pb $L(\mathcal{X}) = || b - h( \mathcal{X})||^2_{\Sigma}$ Gauss Newton or LM are used
* Maximum Likelihood $\mathcal{X}^* = \underset{\mathcal{X}}{\argmax}  \ p(\mathcal{X} | z) $

Underwater feature tracking:
* challenges: turbidity, artificial illumination, texture less area
* matching with descriptors = indirect feature tracking: computing distance in two ways 
* klt = direct tracking 
* TURBID dataset: static underwater with artificial turbidity provided by milk dilution between shots
* evaluate indirect tracking methods on static images by comparing statistics on hamming distance ie evaluation of feature distinctiveness
* direct method only with tracking error
* bucketing = divide image in $n$ cells and extract one feature per cell
* KLT method is the best to track more features
* perpective: experiments with deep learning based feature tracking like DELF or Superpoint

Robust Underwater SLAM:
* propose a KLT based mono slam with a retracking strategy, more accurate and robust in underwater datasets
* two thread front end and back end 
* use bearing vector representation to allow every camera model 
* CLAHE = local histogram egalization
* forward backward KLT + Essential RANSAC
* retracking of lost features in a small window
* Pose Estimation with P3P RANSAC + refinement with BA
* initialization: once enough parallax is detected then KF voted and Essential matrix computed