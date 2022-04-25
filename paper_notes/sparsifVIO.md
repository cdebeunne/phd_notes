# Information Sparsification in Visual-Inertial Odometry

Author: Michael Kaess

Year: 2018

Notes:
---

* "To bound computational complexity, fixed-lag
smoothers typically marginalize out variables, but consequently
introduce a densely connected linear prior which significantly
deteriorates accuracy and efficiency"
* sparsification enables to maintain information sparsity, structural similarity and non linearity
* fixed-lag smoothing framework: sliding window
* drawbacks of sliding window:
    * Marginalizes out variable=> fixing linearization points
    * Will not converge to optimal solution as marginalized variables are no longer optimizable
    * prior densely connected => high computationnal cost
* perform VIO with marginalization & sparsification in RT
* VINS MONO stratefy: discard measurements (ie landmarks) for sparsity & marginalize additionnal variables => loose the capabilities of re-estimating the position of the landmarks

Problem:
* window of states $\mathcal{X}_w = \{ \mathcal{K}_w, \mathcal{F}_w, \mathcal{L}_w \}$
* relative IMU meas with "pre integration factors", each landmark is a 3D point in world frame: "stereo projection factors"

System:
* marginalization is done with Schur Complement on linearized information matrix of the markov blanket
* Figure 3 is excellent!
* When a KF is voted, the last one is marginalized with all the landmarks only associated to it, but the other one are kept (unlike VINS MONO and co.)
* topology: independent **unary prior factors** between the frames and **relative pose factors** (interesting) with all landmarks
* Covariances recovery is computed in closed form as measurements models always provide full rank invertibles jacobian

Results:
* odometry drift measurement of 0.3m/170m on hardware demonstration
* most of the time for marginalization is spend on closed form information matrix computation (it seems that it is highly parallelizable?)
* next step: explore new factor graph topologies


Commentaire:
---
* sparsification applied to an odometry system, not a slam
