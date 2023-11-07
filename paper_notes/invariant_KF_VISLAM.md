# Invariant Kalman Filtering for Visual Inertial SLAM

Author: Martin Brossard

Year: 2018

Notes:
---

* Applied recently discovered UKF on Lie Group (UKF-LG)
* Composite manifold $\chi \in SE_{2+p}(3)$ with pose, velocity and lmks:
$$
\chi=\left[\begin{array}{cccccc}
\mathbf{R} & \mathbf{v} & \mathbf{x} & \mathbf{p}_1 & \cdots & \mathbf{p}_p \\
\mathbf{0}_{2+p \times 3} & & \mathbf{I}_{2+p \times 2+p}
\end{array}\right] .
$$
* UKF spares the user from jacobians computation
* compare left and right multiplication: right is better
* $\dot{R} = R (\omega -b_{\omega})_{\times}$
* Random variable on LG with left multiplication by the mean:
$$
\chi=\bar{\chi} \exp (\boldsymbol{\xi}), \boldsymbol{\xi} \sim \mathcal{N}(\mathbf{0}, \mathbf{P})
$$
* Can then define a left-UKF-LG and a right-UKF-LG
* Generates Sigma Points in the lie algebra and then map them into the group
* Propagation and update step
* Simulation + 5 trajectory of EUROC
* runtime pourri (matlab)