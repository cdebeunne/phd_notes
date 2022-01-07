# Real-time Monocular Visual Odometry for Turbid and Dynamic Underwater Environments

Author: Ferrera

Year: 2020

Notes:
---
* Simulated and real data
* Artificial lightening mandatory
* turbidity effects due to floating particles
* front-end with optical flow and back end with bundle adjustment (classic...)

Feature tracking:

* LKT to be robust to repetitive patterns
* Shi and Tomasi algorithm to detect Harris corners
* Benchmark of keypoint + descriptors (ORB, SURF...) and LKT with Harris
* The search for matching descriptors is in 40*40 pixel zone
* Harris corner is the only one to detect enough features per images
* Epipolar check + RANSAC 
* final solution: Harris with LKT

VO:

* pb of LKT: only available for succesive frames. Not robust to dynamic env => need of a retracking mechanism
* Filtering of pts with forward/backward optical flow and essential matrix estimation in a RANSAC fation
* Retracking of lost features by keeping a small window of the most recent frames
* P3P in a RANSAC fation + BA for pose estimation between frames
* KF voting with parallax and number of corespondence 
* Adaptive selection of KF included in the BA pb

Results:

* SVO and LSD require high frame rate
* LSD fails because it is based on strong gradient that are not frequent underwater
* groundtruth with SFM software Colmap
* BoW doesn't work for loop closure

Commentaire:
---
Système trés similaire à PAVO mais bien rédigé. Continuer de lire des paps sur la VO sous marine, un bon exemple de recherche applicative du SLAM