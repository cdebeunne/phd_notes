# HDVIO: Improving Localization and Disturbance Estimation with Hybrid Dynamics VIO

Author: Cioffi

Year: 2023

Notes:
---

* hybrid dynamics model: point mass vehicle model + learned component to model aerodynamics effect
* estimates external forces + robot state
* history of thrust and IMU to predict dynamics
* soa VIMO only consider drône as a point mass without aerodynamics effects
* IMU + thrust commands -> temporal NN
* the TNN needs only position and velocity signals for training (no gt needed)
* dynamic equation:
$$
\dot{\boldsymbol{v}}_{\mathcal{B}_k}^{\mathcal{W}}=\boldsymbol{R}_{\mathcal{B}_k}^{\mathcal{W}}\left(\boldsymbol{f}_{t_k}^{\mathcal{B}}+\boldsymbol{f}_{\text {res } s_k}^{\mathcal{B}}+\boldsymbol{f}_{e_k}^{\mathcal{B}}\right)+\boldsymbol{g}^w
$$
* $\boldsymbol{f}_{t_k}^{\mathcal{B}}$ is the mass normalized thrust, $\boldsymbol{f}_{e_k}^{\mathcal{B}}$ is the external force acting on the platform, $\boldsymbol{f}_{\text {res } s_k}^{\mathcal{B}}$ is a residual term that takes into account aerodynamic effects
* use only the gyro for rotation
* sliding window MAP estimation with vision, pre integ, dynamics and marginalization
* the dynamic residual is the difference between the actual delta position and velocity and the one obtained by integrating dynamic equations with estimated forces using discrete time Euler numerical integration
* TCN = as powerfull as RNN but with less computations
* the loss of the CNN is the same as in the factor graph but opitimising on $\boldsymbol{f}_{e_k}^{\mathcal{B}}$
* Similar perfo of the TCN wrt methods using full state
* TCN exhibits good generalization to situations unseen while training 