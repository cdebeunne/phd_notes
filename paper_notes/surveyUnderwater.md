# A Survey on Real-Time Motion Estimation Techniques for Underwater Robots

Author: Ferreira

Year: 2014

Notes:
---
* Testing of several feature extraction and matching
* Dopler Velocity Logger (DVL) gives direction and speed of the robot
* Real time motion with software
* Test algorithm implemented in OpenCV
* At that time Binary features (BRIEF)new

Feature Detection:
* Template extraction, extraction of high spatial wavelength and high variance templates
* Shi-Tomasi = improvement of Harris corner detector based on hessian matrix
* SIFT based on difference of the image convolved with different gaussian kernel
* SURF similar to SIFT with higher robustness to scale change
* FAST if at least n contiguous pixels in a circle are darker than a threshold (Accelerated Segment Test), it is considered as a feature best for n=9
* Laplacien $L(x,y) = \frac{\partial^2 I(x,y)}{\partial x^2} + \frac{\partial^2 I(x,y)}{\partial y^2}$
* STAR computation of Laplacian of Gaussian in a star shape => avoid subsampling + non maxima suppression
* ORB like fast but with an orientation operator
* AGAST like FAST but with an adaptative decision tree
* BRISK like FAST but performed at different scale 

Descriptors:
* For template, the normalized correlation is used between the patches
* SIFT based on the gradient orientation histogram in a subregion of 4x4 pixels
* SURF based on Haar wavelet response in the neighbourhood, and nearest neighbour approach
* BRIEF binary descriptor that are compared with a serie of XOR operation = computationnaly efficient
* ORB = rotated brief, improvement of brief that takes roation into account
* BRISK = rotated BRIEF with a method based on orientation computation with a sampling of points
* FREAK = binary, bio-inspired : like brisk but the sampling is more concentrated in the center, coarse to fine search

Motion Estimation:
* Front end of a real time SLAM with feature tracker and laser + acoustic altimeters
* Gives the depth of pixel Z
* Vehicle model based on constant heading and altitude
* Estimation of the speed with a least square approach and motion model

Experiments:
* Images aquired at 5Hz, 360*272 pixels
* too much tuning for SURF, SIFT, STAR, FAST
* poor performance of FAST with floating descriptor but way better with BRIEF
* STAR+BRIEF = fastest approach (1.47Mp per sec)
* STAR detector looks the best
* Template corelation beats every floating point approach
* Binary descriptors are the best
