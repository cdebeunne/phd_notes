# A Novel Parametrization of the Perspective-Three-Point Problem for a Direct Computation of Absolute Camera Position and Orientation

Author: Scaramuzza

Year: 2011

Notes:
---

* direct computation of pnp without using camera frame
* Summary of the pb *Given the relative spatial locations of n control
points, and given the angle to every pair of control points
Pi from an additional point called the center of perspective
C, find the lengths of the line segments joining C to each of
the control points.*
* DLT or homography were first solutions to pnp
* standard approach: p3p in a RANSAC scheme, then pnp on all inliers
* first define a temporary camera frame $\tau$ with two features vectors $f_1, f_2$
* then define a world frame $\eta$ with 3D points $P_1, P_2, P_3$
* then complex trigonometry considerations that leads to a 4 order polynomial
* uses a 4th point to choose between the four solutions
* for pnp problem, only homogeneous coordinates are used, so no need for Calibration matrix 
* experiments: synthetic points projected on image, gaussian noise added, then homogeneous coordinates computed
