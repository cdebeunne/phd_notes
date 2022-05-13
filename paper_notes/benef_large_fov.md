# Benefit of Large Field-of-View Cameras for Visual Odometry

Author: Zhang

Year: 2016

Notes:
---
* impact of fisheye or catadioptric on the quality of motion estimate of urban and indoor scene 
* experiment checking the keypoint tracking accuracy (in pixel) wrt number of frame of the trajectory -> less accuracy with big FOV
* when the FOV gets bigger, the angular resolution gets smaller
* experiments solving the absolute pose estimation (pnp) problem with noisy landmarks
* experiments with a full VO pipeline: large FOV are better in confined environnement 

SVO for omni cam:
* to change: implementing camera models + reprojection error with bearing vectors + sampling on epipolar curve
* choose of an error metric for bearing vector errors -> bearing vector error is the best
* sample pixel on the epipolar line => sample pixels between $f_{min}, f_{max}$ the bearing vectors representing the depth interval we search in
 