# Stereo Vision and Rover Navigation Software for Planetary Exploration

Authors: Mark W. Maimone, Larry Matthies, Steven B. Goldberg

Notes:
----

Stereo operations:

* Downsampling from 1024x1024 to 256x256
* Integer operation for epipolar search
* Compute the laplacian for pixel intensity bias with difference of gaussian - in fact the corelation is performed on the laplacian image
* Corelator that assign a score to each pixel in a 7x7 window then range is estimated with the disparity of the maximum scored pixel
* peak filtering & co to check the validity of the range
* (X,Y,Z) mapping for each valid pixel with camera model
* comparison of code performance on individuals operation => vectorization of oparations with assembly 

GESTALT navigation system:

* Input: state of the world allready seen, discrete set of (X,Y,Z) points and waypoint goal
* Cells size of a rover wheel
* For each cells compute mean, cov and number of points and fit a plane
* Then compute hazard measures: step (elevation between pairs of pts), roughness (residual of the planar fit), pitch (slope), border 
* Arc hazard vote + waypoint arc vote

Commentaires:
---
Bonne compréhension des systèmes, mais un peu limite sur le hardware et la vectorization en assembleur (???)