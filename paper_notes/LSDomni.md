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