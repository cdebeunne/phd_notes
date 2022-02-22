# Large-Scale Direct SLAM for Omnidirectional Cameras

Author: Cremers

Year: 2015

Notes:
---
* formulation with the unified omnidirectionnal model
* more robust to degenerate (rotation only) movement
* Exp with a fisheye with a 185° FOV
* EKF for omni cameras: *Adapting a
real-time monocular visual slam from conventional to omnidirectional
cameras*
* evaluation of the SLAM for the three camera models

Camera models:
* A camera models is a function $\pi : \mathbb{R}^3 \rightarrow \Omega$
* Single viewpoint assumption: all light rays pass through a single point in space, the origin of camera C
* Image rectification: given two projection function $\pi_1, \pi_2$
$$
I_2(u,v) = I_1(\pi_1(\pi_2^{-1}(u,v,1)))
$$
* Array of pinhole: array of pinhole cameras which have the same principal point but different orientations. Here, 6 cameras that forms a cube shaped image plane are chosen
* It is linear and easy to compute but there are discontinuities and it doesn't fit natural lenses
* For SLAM the model and its derivative must be fast to compute 
* Unified model: project on a unit sphere then a pinhole projection shifted by $\xi$ from the center of the sphere

Direct omnidirectionnal SLAM:
* each KF contains a probabilistic semi-dense inverse distance map (inverse distance instead of depth to take point behind the cam)
* SE(3) tracking with direct image alignement
* Estimated distance map using small baseline stereo comparison
* Scale drift pose graph between KF
* initialization with a random distance map with large covariance 
* direct alignement with direct minimization of photometric error
$$
\mu \in \mathfrak{se}(3), \mathbf{u} \in \Omega, r_\mathbf{u}(\mu)
= I_{kf}(\mathbf{u}) - I_{new}(\pi(\omega(\mu,\mathbf{u})))
$$
where $\omega$ unproject a point and transform it by $\mu$
* Then this residual is iteritavley minimized, with a costly reevaluation of Jacobian at each iteration
* To reduce computations the jacobian is evaluated once by applying the inverse of the increment on the pixel of the KF => thus the jacobian doesn't depend on current state
* Sim(3) takes into account changes in scale between images depth map
* Non-rectified stereo by defining two points on the unit sphere (between lower and upper bound of disparity) and parametrizing the straight line between them but it becomes very costly for large disparity search
* Comparison of performances with pre image rectification

Results:
* Images are cropped and scaled to a 480*480 region around the center
* omni outperform pinhole cam => 3D points are visible for a longer time
* a large FOV can be more important than high image resolution

Commentaires:
---

Papier hyper important, c'est exactement ce que je veux faire avec le slam de Damien