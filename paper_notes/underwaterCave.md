# Underwater Cave Mapping using Stereo Vision

Author: Weidner

Year: 2017

Notes:
---
* Volumetric model with stereo and light beam
* In underwater robotic: 2.5D maps or image mosaics for SLAM
* Interesting related works
* Problem of lighting variations beacause of divers light beam: brightness Constancy Constraint is violated
* contour tracking: Canny edge detector on a thresholded binary image to select the area of the light beam
* sparse reconstruction: Stereo matching with SURF descriptor and epipolar search on contour pixels
* dynamic environnement with bubbles
* Visual odometry performed with OrbSLAM2