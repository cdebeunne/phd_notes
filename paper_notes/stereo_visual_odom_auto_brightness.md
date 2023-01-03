# Stereo Visual Odometry with Automatic Brightness Adjustment and Feature Tracking Prediction

Author: Yin

Year: 2022

Notes:
---

* Classic indirec VO alhorithm with brightness adjustement (using an histogram matcher to predict the exposure of the image) + reliable feature point prediction (using constant acceleration model + stereo geometric constraint) to improve KLT tracker
* Marginalization also (maybe the first example of vision only marg)

### Related Work:

* PL SLAM = Orbslam2 with line features
* Geometric Corespondence Network (GCN) = CNN that produces point correspondence
* *Joint radiometric
calibration and feature tracking system with an application to stereo* = example of exposure estimation

### Front end 
* brightness adjustement, feature tracking, motion estimation 
* Brightness adj : 
    * grayscale histogramm doesn't change that much at 10-20 Hz
    * use instead the cumulative histogram $h$ (i.e. the probability that a pixel value is less than or equal to the given value)
    * 3 parameters to evaluate the brightness: $a_{mean}, a_{half}$ and $a_{double}$ with $h(a_{mean}) = 0.5$ and so on
    * Compute a coeff based on these param to evaluate if the brightness needs to be adjusted 
    * the comparison is done on the 20 previous frames
* feature position prediction:
    * ORB SLAM uses a constant velocity assumption to guide the search 
    * Here uses constant acceleration instead (better for dynamic motion like drones)
    * simplification are made here: the increment in translation are equals, the axis of the rotation is always the same and the increments in angle of rotation are equals 
    * with this: predict the current pose, project all the landmarks in the current image and init a KLT tracker 
    * Outlier rejection using essential matrix prediction
* motion prediction is perform with single frame BA with huber loss to reject outliers 

### Back-end 
* KF vote with 30 pixels parallax or less than 80 tracked lmk
* inverse depth parametrization of lmk
* Example on marginalization completely wtf
* wrong expression on the prior residual eq 17 (apparently ?)

### Experiments
* ablation studies (ie disabling novelties)
* interesting figure to represent running time of all the subsystems
* EUROC + KITTI comparison 