# On-Manifold Preintegration for Real-Time Visual-Inertial Odometry

Author: Forster

Year: 2015

Notes:
---

* Code available: https://bitbucket.org/gtborg/gtsam/src/develop/gtsam/navigation/ManifoldPreintegration.cpp
* pre integrated measurement: combining inertial measurements to generate a relative pose constraint between two poses 
* theory that adresses the manifold structure of $SO(3)$ => avoids singularities as with Euler angles
* structureless visual factor => full batch slam

## Pre-integration
* naive preintegration leads to re integring the deltas when the linearization point changes (when the orientation changes, it has to be propagated in the integration of the p)
* It uses the following deltas:
$$
\Delta \mathrm{R}_{i j} \doteq \mathrm{R}_i^{\top} \mathrm{R}_j \\
\Delta \mathbf{v}_{i j} \doteq \mathbf{R}_i^{\top}\left(\mathbf{v}_j-\mathbf{v}_i-\mathbf{g} \Delta t_{i j}\right) \\
\Delta \mathbf{p}_{i j} \doteq \mathbf{R}_i^{\top}\left(\mathbf{p}_j-\mathbf{p}_i-\mathbf{v}_i \Delta t_{i j}-\frac{1}{2} \mathbf{g} \Delta t_{i j}^2\right)
$$
* BEWARE: the deltas on velocity and position do not corespond to physical deltas, it simply enables to compute the measurement independantly of the state
* It is needed to compute the covariance of this delta: it is shown that it is a linear form of IMU measurement noises. It can be computed using a simple linear propagation
* A slight update of the delta is performed during optimization using a first order approximation of the delta wrt the bias
* This bias updates are performed in the residual evaluation
* Bias residual: noise defined as integrated white noise i.e
$$
\left\|\mathbf{r}_{\mathbf{b}_{i j}}\right\|^2 \doteq\left\|\mathbf{b}_j^g-\mathbf{b}_i^g\right\|_{\Sigma^{b g d}}^2+\left\|\mathbf{b}_j^a-\mathbf{b}_i^a\right\|_{\Sigma^{b a d}}^2
$$
with $\Sigma_{bgd} = \Delta t_{ij} Cov(\eta_{bg})$ 

## Structure less visual factor

* The idea is to create a visual factor that does not depend on the landmark position
* The trick here is to apply directly the optimal pose of the landmark in the cost function
* First, the visual cost is linearized:
$$
\sum_{l=1}^L \sum_{i \in \mathcal{X}(l)}\left\|\mathbf{F}_{i l} \delta \mathbf{T}_i+\mathbf{E}_{i l} \delta \rho_l-\mathbf{b}_{i l}\right\|^2
$$
* Then the factors of a given landmark $l$ are grouped in a matrix form:
$$
\sum_{l=1}^L\left\|\mathbf{F}_l \delta \mathbf{T}_{\mathcal{X}(l)}+\mathbf{E}_l \delta \rho_l-\mathbf{b}_l\right\|^2
$$
* The optimal value of $\rho_l$ is computed:
$$
\delta \rho_l=-\left(\mathbf{E}_l^{\top} \mathbf{E}_l\right)^{-1} \mathbf{E}_l^{\top}\left(\mathbf{F}_l \delta \mathbf{T}_{\mathcal{X}(l)}-\mathbf{b}_l\right)
$$
* Finally it is backprojected in the cost function to generate the final residual:
$$
\sum_{l=1}^L\left\|\left(\mathbf{I}-\mathbf{E}_l\left(\mathbf{E}_l^{\top} \mathbf{E}_l\right)^{-1} \mathbf{E}_l^{\top}\right)\left(\mathbf{F}_l \delta \mathbf{T}_{\mathcal{X}(l)}-\mathbf{b}_l\right)\right\|^2
$$
* All the landmarks are then triangulated again with the optimized poses

## Experiments
* ISAM2 has a constant execution time wrt to full batch
* Demonstrate the first order approximation of the bias variation comparing a reintegration (gt) and the first order approximation with monte carlo experiments
* The gimball lock => misestimation of the covariance around a pitch angle of 90 degree
* SVO = feature tracker based on sparse image alignement i.e. features are tracked minimising photometric error instead of klt. It is used as the front end that outputs selected keyframes and the set of triangulated points
