# Binocular Spherical Stereo

Author: Shigang Li

Year: 2008

Notes:
---
* uses spherical camera model
* conversion to longitude/lattitude images to get epipolar lines
* In the case of a fisheye image depth (*z* coordinate) != distance (rho in spherical coords)
* The disparity is the difference between length of arcs d = f(theta_l - theta_r)
* Images need to be rectified: a rotation matrix is computed thanks to a calibration process that can map the pixels of a camera so that the frames of both images are aligned
* High computational cost of searching along epipolar curves => creation of a latitude longitude image
* Simulation to study the error factors for distance computation: blind spot around the epipoles 