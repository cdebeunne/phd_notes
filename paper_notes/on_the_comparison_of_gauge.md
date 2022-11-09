# On the Comparison of Gauge Freedom Handling in Optimization-based Visual-Inertial State Estimation

Author: Zhang

Year: 2018

Notes:
---

* Three solutions: fixing the unobservable states, setting a prior or let them free
* Accuracy similar but leads to different covariance estimation
* 4 DoF: Global position and yaw are unobservable (pitch and roll are provided by IMU)
* The objective function $J$ is invariant to certain transformations $g$ of parameter $\boldsymbol{\theta}$ i.e.
$$
J(\boldsymbol{\theta}) = J (g(\boldsymbol{\theta}))
$$
* The orbit associated to $\boldsymbol{\theta}$ is the 4D manifold:
$$
\mathcal{M}_{\theta} = \{ g(\boldsymbol{\theta}) | g \in \mathcal{G} \}
$$
* Fixating the yaw in increment is not efficient as with propagation of updates, the yaw wrt the origin will change
* *Gauge Fixation* = fixing the position and yaw of the first pose = setting the jacobians of the corresponding columns to zero
* *Gauge prior* = let's add a penalty
* The prior weight needs to be properly tuned to not make too much iterations: 10^5 is great
* Covariance on free gauge is more distributed and has not meaningfull geometrical value