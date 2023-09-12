# Associating Uncertainty to Extended Poses for on Lie Group IMU Preintegration with Rotating Earth

Author : Brossard

Year : 2021

Notes:
---
* $SE_2(3)$ represents orientation, velocity and position. Also called "extended pose"
$$
S E_2(3):=\left\{\mathbf{T}=\left[\begin{array}{c|c|c}
\mathbf{R} & \mathbf{v} & \mathbf{p} \\
\hline \mathbf{0}_{2 \times 3} & \mathbf{I}_2 
\end{array}\right] \in \mathbb{R}^{5 \times 5} \mid \begin{array}{c}
\mathbf{R} \in S O(3) \\
\mathbf{v}, \mathbf{p} \in \mathbb{R}^3
\end{array}\right\}
$$
* addresses uncertainty propagation, pre integration on manif
* defines extended pose integration as 
$$
\mathbf{T}_{i+1}=\boldsymbol{\Gamma}_i \Phi\left(\mathbf{T}_i\right) \mathbf{\Upsilon}_i
$$
with 
$$
\begin{aligned}
\Phi_t(\mathbf{T}) & :=\left[\begin{array}{c|c}
\mathbf{R} & \mathbf{v} \mid \mathbf{p}+t \mathbf{v} \\
\hline \mathbf{0}_{2 \times 3} & \mathbf{I}_2
\end{array}\right], \\
\boldsymbol{\Gamma}_t & :=\left[\begin{array}{c|c}
\mathbf{I}_3 & \operatorname{tg} \mid \mathbf{g} t^2 / 2 \\
\hline \mathbf{0}_{2 \times 3} & \mathbf{I}_2
\end{array}\right], \\
\mathbf{\Upsilon}_t&:=\left[\begin{array}{c|cc}
\Delta \mathbf{R}_t & \Delta \mathbf{v}_t & \Delta \mathbf{p}_t \\
\hline \mathbf{0}_{2 \times 3} & \mathbf{I}_2
\end{array}\right]
\end{aligned}
$$
* Derives a noise model as:
$$
\boldsymbol{\Upsilon}_i:=\hat{\boldsymbol{\Upsilon}}_i \exp \left(\boldsymbol{\eta}_i\right), \quad \boldsymbol{\eta}_i \sim \mathcal{N}\left(\mathbf{0}_9, \mathbf{Q}\right)
$$
* Compute a closed form formula for uncertainty propagation
$$
\boldsymbol{\Sigma}_{i+1}:=\mathrm{E}\left[\boldsymbol{\xi}_{i+1} \boldsymbol{\xi}_{i+1}^T\right] \stackrel{(42)}{=} \underbrace{\mathrm{Ad}_{\hat{\boldsymbol{\Upsilon}}_i^{-1}} \mathbf{F}}_{:=\mathbf{A}_i} \boldsymbol{\Sigma}_i\left(\operatorname{Ad}_{\hat{\boldsymbol{\Upsilon}}_i^{-1}} \mathbf{F}\right)^T + Q + S_{4th}
$$
* The 4th order term is due to derivation with the BCH formula and leads to more accuracy wrt to monte carlo covariance
* On simulations $SE_2(3)$ representation leads to a banana shaped uncertainty while $SO(3) \times \mathbb{R}^6$ leads to a gaussian
* Proposes a IMU pre integration in $SE_2(3)$ that leads to the following measurement:
$$
\mathbf{\Upsilon}_{i j} =\left(\boldsymbol{\Gamma}_{i j} \Phi_{i j}\left(\mathbf{T}_i\right)\right)^{-1} \mathbf{T}_j
$$
* Same pre integration measurement as in *Foster et al* but uncertainty is encoded in $SE_2(3)$
* Compare approaches by deriving IMU measurements on a KITTI trajectory by differentiating groundtruth
* $SE_2(3)$ is the most consistent approach according to the NEES criterion, while *Forster et al* approach degrades for long integration time
* Add random bias peturbation on measurements from KITTI, and it is more accurate for pose and velocity correction but similar for rotation
* IMU equations taking earth rotation into account:
$$
\begin{aligned}
\dot{\mathbf{R}} & =-\boldsymbol{\Omega}_{\times} \mathbf{R}+\mathbf{R}\left(\boldsymbol{\omega}^m-\mathbf{b}^{\boldsymbol{\omega}}-\eta^{\boldsymbol{\omega}}\right)_{\times} \\
\dot{\mathbf{v}} & =\mathbf{R}\left(\mathbf{a}^m-\mathbf{b}^{\mathbf{a}}-\eta^{\mathbf{a}}\right)+\mathbf{g}-2 \boldsymbol{\Omega}_{\times} \mathbf{v}-\boldsymbol{\Omega}_{\times}^2 \mathbf{p}, \\
\dot{\mathbf{p}} & =\mathbf{v}.
\end{aligned}
$$
* Obtain pre integration factors takin earth rotation into account that do not change the covariance formulas (as is corresponds only to non noisy additive terms)
* Implement it in GTSAM and performs a 4H (~150km) drive to test long term LiDAR-Inertial navigation using a fixed lag smoother based on ISAM2
* The factor graph is fed with: pre integration factors, translationnal factors (from LiDAR) and zero upward velocity factor
* LiDAR uses scan matching algorithm (whose orientation uncertainty is way higher than the one of IMU integration)
* A Huber loss is used for the translationnal factor to mitigate outliers
* Taking into account earth rotation seems beneficial for sequences of length more than 7 minutes
