# Adaptive Localization and Mapping with Application to Planetary Rovers

Author: Carrio

Year: 

Notes:
---
* Full graph optimization based on improved wheel odometry model and visual features
* error model of odometry based on Gaussian Process 
* Adapt the frame rate to provide only highly informative KF

## Intro:
* 60% of overlapping is needed to perform VO (why?)
* Post 2020 missions plan to cross 20km in 6 months (vs 15 km in 7 years for MER) (super interesting figure describing all the past and futur missions)
* Need for mapping for futur missions of sample fetching or human base construction
* Without SLAM, world = "infinite corridor" for the robot

## Related Work
* SAPP = localization system on MER and MSL
* It combines gyro (for attitude), VO (relative displacement when high slippage is predicted), accelero (for gravity estimation) and WO
* Lots of literature on legged wheel odom
* Slippage can be detected using the motor current 
* GP applied to learn residuals, here to learn a slip vector
* Active SLAM = selecting a maximal informative motion command in the control of the plateform

## Methodology
* WO + inertia = most common technique for dead reckonning 
* Need to define: Base frame, A_i wheel frame, C_il contact point frame of each wheel
* The jacobian Matrix J_il relates the motion of a single contact point to the body motion
* Navigation kinematics relates the rover pose rates (i.e. $[\dot{x}, \dot{y}, \dot{z}, \dot{\theta}, \dot{\phi}, \dot{\psi}]$) to sensed rate quantities
* An optimal solution combining the contribution of each wheel is computed, but a poor measurement on a wheel may degrade the solution => a weight matrix based on the normal forced sensed on each wheel is computed
* But a force sensor is not always available => quasi static force estimation
* Each contact force is estimated using the quasi static assumption 

## GP regression of odom errors
* (X,Y) training data that are illustrated with a noisy function $y_i = f(x_i) + \epsilon$
* The prediction is a multivariate gaussian as:
$$
p(Y \mid X)=\mathcal{N}(0, K(X, X)+\Sigma)
$$
* With $ K_{ij} = \sigma_f^2 e^{-\frac{1}{2}\left(\boldsymbol{x}_i-\mathbf{x}_j\right) \mathbf{W}\left(\boldsymbol{x}_i-\boldsymbol{x}_j\right)^{\top}} $ the kernel that measures the closeness between points and $\Sigma$ a diagonal covariance matrix
* For any arbitrary $\boldsymbol{x}^*$ its mean and variance can be predicted with the GP hyperparameters (W, $\sigma_f$, $\Sigma$) and training data
* And the hyperparameters can be learned maximising the log likelihood of the training outputs of the given inputs
* The purpose of GP here is to model the odometry error to feed the backend of the SLAM, thus $x_i = [s(i), u(i)]$ and $y_i = s(i+1) - s(i) - g(s(i), u(i))$ with $g$ the motion model of the rover