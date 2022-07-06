# Sliding Window Filter with Application to Planetary Landing

Author: Gabe Sibley

Year: 2010

Notes:
---
* sliding window filter based on delayed state marginalization
* the goal is a constant-time algorithm
* EDL (entry - descent - landing)

three-part problem formulation:
* distinction between: prior, measurements and process model
* the prior is about the first pose and the map (How do we process a prior in optimization?)
* Gauss Newton method is locally q-quadratically convergent to the map estimate for near zero residuals pb
* $J^T \Sigma^{-1} J$ ie. the Hessian approximate is the Fisher Information Matrix 
* Strucutre of Jacobians:
    * H (for meas) is very sparse but large (due to the nb of meas) 
    * L (for prior) is only made of identity bloc
    * D is made of identity and jacobians of the motion model
* The sparsity pattern of the total information matrix affect the complexity
* Directly removing parameters can lead to overconfidence => marginalization

Overview:
* In Gauss Newton method, the covariance is approximated by the Hessian
* In SWF if k=1, this is equivalent to iterative EKF
* Use of a robust Huber Kernel
* Effect of marginalization:
    * fill in in the global information matrix 
    * pose to landmark conditionnal dependence => encodes rigidity constraint 

Experiments:
* Flea cams in stereo config and narrow FoV, 15 Hz
* Fixed measurement track in front of a wall
* Front end with feature patch matching of Harris Keypoints
* Matching: emlpoy all pair matching, then Moravec consistency method with consistency matrix to identify the correct set of inliers 
* for surface reconstruction groundtruth, they consider the wall being flat (after verification with fiducial markers)
* sparse marginalization: build the prior only with diagonal entries of Schur Complement 

Discussion:
* KF is only optimal for linear pb
* SWF is equivalent to "order k" iterated EKF
* arguments in favor of estimation > filtering 
* future work = smart marginalization
