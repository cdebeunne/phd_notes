# Robust 6DOF Motion Estimation for Non-Overlapping, Multi-Camera Systems

Author: Clipp

Year: 2008

Notes:
---

* pose estimation with scale with non overlapping FoV setups
* assumption: 5 temporal correspondences in cam + 1 corespondence in any additional camera
* Derive the expression of the scale using a single point correspondence $x \leftrightarrow x'$ :
$$
\lambda = -\frac{x'^TAx}{x'^TBx}
$$
* Geometrical explanation: the view of a 3D point seen from the first camera crosses a plane made by the different $C_2(\lambda)$ and the ray of $x'$ noted $v'$. The $v'$ that points to this intersection point fixes the scale
* Critical configurations:
    * $v$, $v'$ and $C_2'(\lambda)$ can't be coplanar
    * Far away points ($\pi$ and $v$ are parrallel)
    * The axis of rotation is perpendicular to the plane made by $C_2, C_1'$ and $C_1$
* Check for critical configurations: double the scale and check if there is still a big fraction of inliers

Algo:
---
* 5pt algorithm + RANSAC + Chirality check to estimate motion up to scale
* One point RANSAC + pbM estimator to recover scale
* Inlier correspondences on the second camera are determined using the distance to epipolar lines
* then a linear least square calculation of the scale factor is made with inlier correspondences
* Then a bundle adjustement of the full multi camera system is performed

Exp:
---
* simulations experiments with randomly generated points in a cube
* real experiments using 8 cameras
* Only the scale degrades when the motion becomes ambiguous