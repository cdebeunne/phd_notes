# Direct Sparse Odometry

Author: Engel & Cremers

Year: 2016

Notes:
---

* Do not depend on keypoints & descriptors => acheive real time
* Indirect method: pre processing of raw measurment to compute intermediate values
* Direct methods use the raw sensor measurements
* Direct => photometric error, indirect => geometric error 
* Dense method exploit the connectedness of pixels => a geometric prior for smoothness 
* Benefit of direct formulation = a pixel does not need to be recognizable by itself
* Dense formulation => correlation between pixels that makes the probability distr intractable 
* Common features descriptors and detectors invariant to photometric variations 

Photometric calibration:
* non linear response function and lens attenuation (vignetting) => impose photometric correction to each image 

Model formulation:
* photometric error of a point is a weighted SSD (?) on a neighbourhood of pixels
* weighting based on brightness funciton parameters, time exposure and pixel gradient
* inverse depth parametrization of points

Optimization:
* Windowed optimization in a gauss newton scheme 
* "First evaluate Jacobians" = evaluating geometric and photometric jacobians at x=0 as these are smooth functions 
* Marginalization of old variables with the Schur Complement
* Marginalization = "elimination of states in nonlinear optimization"

VO front-end:
* determining the set of points w/ outlier rejection and occlusion detection
* good initialization is necessary so that the linearization remain good (rule of thumb: linearization valid in 1-2 pixel radius)

Frame management:
* 7 active KF all the time
* Initial frame tracking is performed with two frame direct image alignement with constant velocity model
* lots of KF in the beginning then it is sparsified
* KF creation with optical flow and exposure time values
* marginalization strategy: if less than 5% of keypoints are shared with the last KF and wrt to the euclidean distance
* Np = 2000 active points in all active KF, at each KF: -> 2000 points are selected  (well distributed, with high gradient)

-> these are tracked in subsequent frames (on epipolar line, minimizing photometric error) to compute a coarse depth value

-> then 2000 points are selected on all active KF and added to optimization pb

Analysis:
* Direct methods models photometric noise ie additive noise on pixel intensity while Indirect methods models geometric noise ie noise on (u,v) coords of pixels
* Direct method works well with camera designed for computer vision as the geometric noise is corrected 
* Hihgly non convex pb du to the image parameters included in the cost function
