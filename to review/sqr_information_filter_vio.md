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

Sum up:
---
This paper presents a filtering based visual inertial state estimator designed to operate on resource constrained computers. It presents an original Multi State Constrained Kalman Filter (MSCKF) architecture that updates a square root information matrix to handle single precision numbers. Stochastic cloning is performed via Gaussian elimination to estimate the time offset of the VI hardware and to change the anchor of long tracked features. A fast outlier rejection scheme based on an approximation of the Mahalanobis distance is implemented to reduce the run time of the filter. A contribution is also proposed concerning feature tracking. To limit the drift accumulated by sparse optical flow tracking, the author propose to refine tracks by computing analyticaly an affine transform between patches on different views before tracking on a warped patch. An experimental study of the proposed system is conducted on the EUROC benchmark using the stereo VI setup. It is on par for the ATE metric with BASALT that represents SOTA for optimisation based VIO and OpenVINS that serves as a reference for filtering based VIO. An ablation study demonstrates the gain in accuracy with affine optical flow and a run-time study shows that this method is significantly faster than OpenVINS. 