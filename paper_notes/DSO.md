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
