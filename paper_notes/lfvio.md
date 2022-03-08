# LF-VIO: A Visual-Inertial-Odometry Framework for Large Field-of-View Cameras with Negative Plane

Year: 2022

Author: Wang

Notes:
---

* when fov is larger than 180° reaches negative plane -> [u,v,1]^T cannot be used 
* feature points rps with unit vectors
* public fisheye dataset PALVIO
* SVO, VINS Mono, ORBSLAM 3 support fisheye camera models
* KLT sparse flow, RANSAC
* Epipolar geometry to initialize, + Epnp to initialize depth of features 

Panoramic SLAM:
* PAL SLAM with panoramic annular cameras
* many converts it to pinhole model => doesn't enable very wide FOV

System:
* Shi Tomasi Corners
* Unified spherical model for cameras with OmniCalib toolbox (Scaramuzza)
* Epipolar -> Triang -> Epnp -> global BA
* classic init procedure

Experiments:
* LVI SAM dataset for public fisheye dataset (single camera...)
* investigating different FOV => whole FOV offers best performances
* Comparison with SVO2.0 and VINS-Mono
* Future work: adding stereo and LiDAR
