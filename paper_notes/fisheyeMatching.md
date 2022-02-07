# Spherically Optimized RANSAC Aided by an IMU for Fisheye Image Matching

Author: Liang

Year: 2021

Notes:
---
* image matching method: use fisheye spherical coordinate and provide relative rotation with IMU to get pose estimation and mismatch removal.

Related work:
* references of image matching for fisheye using rectified image (but lose of FOV, and image artifacts)
* Spherical SIFT, omni SIFT and also affine invariant detector (hessian affine)
* many sensor fusion methods
* many deep learning based methods

System:
* Use the polynomial fisheye model of openCV
* Use the spherical model for estimating Essential matrix
* hypothesis: when IMU and camera are fixed rotation obtained by the camera is the one of the IMU (no calibration needed)
* four point method with RANSAC (one parameter being fixed by IMU)

Experiments:
* Evaluation with soa algorithm on the matching success rate
* Discussion about IMU noise by adding noise on transformations obtained with MARG => very interesting

Commentaire:

Article modeste mais trés intéressant