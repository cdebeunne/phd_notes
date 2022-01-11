# The Relocalization of SLAM Tracking Based on Spherical Cameras

Author: Chang

Year: 2021

Notes:
---
* Relocalization based on features with spherical cameras
* Feature extraction with deep learning
* Setup with 8 fisheye lenses
* relocalization = estimate the 6DoF pose of a camera in a known env

Calibration of the setup:
* Extract keypoints with SIFT
* calibration patterns = chess board placed all around the camera module
* non linear distortion model
* stitching all the images to a panoramic image

CNN for features description on panoramic images:
* Classic CNN deosn't perform well on panoramic images
* Adaptation of CNN for perspective images to panoramic
* Simplification of GeoDesc to meet real time requirement + panoramic dataset
* Taking the middle of the image in practice to remove high distorted areas

Relocalization:
* Using a SfM point cloud to reoptimize the tracking 
* Features matching with the descriptors of the SFM pointcloud

Commentaires:

Super boulot de déploiment d'un système fisheye, mais papier pas hyper clair