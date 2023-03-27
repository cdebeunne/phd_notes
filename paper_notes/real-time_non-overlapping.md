# Real-Time 6D Stereo Visual Odometry with Non-Overlapping Fields of View

Author: Tim Kazik

Year: 2012

Notes:
---
* monocular VO for each cameras and the metric scale is recovered with known transfo between cameras
* Method to improve the FOV wrt stereo setup
* RANSAC scheme on a window of frames for scale estimation

Related Works:
---
* *Robust 6DOF Motion Estimation for Non-Overlapping, Multi-Camera Systems* using a single point to estimate the scale
* *Visual Odometry for Non-Overlapping Views Using Second-Order Cone Programming* transforms motion estimation into a triangulation pb
* other methods use the Global Camera Model (GCM) treating the cameras as a single one

Metric Scale Estimation:
---
* estimate both left and right scale factors $\mu$ and $\lambda$ with 
$$

\left[\begin{array}{ll}
\mathbf{R}_{\mathrm{LR} \mathrm{R} 2} \mathbf{t}_{\mathrm{R} 2 \mathrm{R} 1} \quad{ -}_{\mathrm{L} 2} \mathbf{t}_{\mathrm{L} 2 \mathrm{~L} 1}
\end{array}\right]\left[\begin{array}{l}
\lambda \\
\mu
\end{array}\right]=\left(\mathbf{R}_{\mathrm{L} 2 \mathrm{~L} 1}-\mathbf{I}_{3 \times 3}\right)_{\mathrm{L}} \mathbf{t}_{\mathrm{LR}}

$$
* Consider multiple constraints on the last N poses then solve the problem on an augmented LS problem
* Frame outliers can be due to degenerate motion (c.f. Robot *Hand-Eye
Calibration Using Structure-from-Motion*) or wrong motion estimate => RANSAC scheme

Fusion Of the two VO:
---
* The motion of the two VO are fused: the two motion are expressed in a common frame, the corresponding covariance matrices are computed, the motion are fused in the common frame and the fused motion is transformed back in both individual frames
* The covariance is obtained via the Hessian Matrix of the reprojection error at the minimum of the cost function
* Fuse the measurements with an EKF

Experiments:
---
* *Using Many Cameras as One* demonstrated that two cameras with opposite directions is the best setup
* Calibration using a tracked checkboard 
* Compared the two VO with scale initialized with GT, the VO with scale estimation and the VO with scale estimation + fusion