# A Stochastic Cloning Square-Root Information Filter with Accurate Feature Tracking for Visual-Inertial Odometry

Author: Hu

Year: 2024

Notes:
---
* keep updated the square root matrix instead of the Hessian to reduce the numerical precision
* uses stochastic cloning to estimate time offset between IMU and camz
* warp image patches with affine transform to robustify frame to frame data association
* propose a novel analytical derivation of the affine transform between feature patches
* Gaussian elimination: transforming a LS problem under constraints into two subproblems on two subsets of the variables
* clone variables to estimate the time offset between IMU and cam $t$. The IMU propagation gives a pose $x_1$ and the pose of the camera can be estimated as $x_2 = x_1 + J_t t$
* Use IMU integration to warm start the optical flow est
* The global pipeline is not clearly explicited, this makes the paper hard to read, even for a reader used to visual state estimation
* State of msckf: current IMU state, time offset, a set of inverse depths, a clone of k poses
* Which states are chosen to be included in the sliding window?

## Sum up
This paper presents a filtering based visual inertial state estimator designed to operate on resource constrained computers. It presents an original Multi State Constrained Kalman Filter (MSCKF) architecture that updates a square root information matrix to handle single precision numbers. Stochastic cloning is performed via Gaussian elimination to estimate the time offset of the VI hardware and to change the anchor of long tracked features. The square root matrix is triangulated with a smart use of block householder triangulation to reduce computations. A fast outlier rejection scheme based on an approximation of the Mahalanobis distance is also implemented to reduce the run time of the filter. A contribution is also proposed concerning feature tracking. To limit the drift accumulated by sparse optical flow tracking, the author propose to refine tracks by computing analyticaly an affine transform between patches on different views before tracking on a warped patch. An experimental study of the proposed system is conducted on the EUROC benchmark using the stereo VI setup. It is on par for the ATE metric with BASALT that represents SOTA for optimisation based VIO and OpenVINS that serves as a reference for filtering based VIO. An ablation study demonstrates the gain in accuracy with affine optical flow and a run-time study shows that this method is significantly faster than OpenVINS. 

## Related Works
Section II highlights a strong bibliographical work on all the contributions brought by the article. It is even possible to remove some redundant citations (e.g. [16] or [35]) if space is needed

## Minor remarks:
* Intro: add upper case to Inertil Measurement Unit (to fit the acronym)
* III - C:  for cloning you express the constraint as x2 = x1 + Jt while for anchor you express it as $x_1 = Jx_2 + J_ox_o$. You should be consistent and write constraints in the same order 
* III - C: "We can also analyze the observation property" you should use the word observability to refer to this concept
* IV - B: An illustration of the procedure would greatly facilitate the reading 
* IV - B: You state that you have observed similar results w.r.t. SVO and PTAM in your experiments, but there is no mention of these experiments in part VI. An illustration or a table should be provided to demonstrate the accuracy of this method.
* Exp: you don't give enough details about the method you compare yourself to. For instance, BASALT is a full mapping pipeline that employs loop closing techniques to refine the trajectory and you seem to have presented the results in VIO mode only
* You show the run-time of OpenVINS and SCRIF with only MSCKF features but you don't display the ATE of those two methods which could be interesting to evaluate the need for SLAM features in the feature

## Conclusion

This paper provides interesting tricks to improve a filtering based VIO. The results are promising and the paper reflects strong technical skills on the subject. However, this paper is too hard to read. It could be enhanced by more explanatory figures and some technical details can be omitted. Too much time is spend to explain matrix triangulation tricks, while it seems to be a minor contribution of the paper. For instance, I suggest the author to remove Figure 3 and shorten paragraph III-D to add an explanatory figure for section IV-D. The experiments section is rigourous but lack a diversity of content. There are only tables without colors or bold values, curves for RMSE or box plot for run-time comparison would really improve the presentation of those good results. This paper deserves important modifications to fit the standard of a top tier conference.