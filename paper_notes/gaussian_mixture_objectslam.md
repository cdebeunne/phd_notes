# Gaussian Mixture Midway-Merge for Object SLAM with Pose Ambiguity

Authors: Jae Hyung Jung

Year: 2022

Notes:
---

* Merge Gaussian Mixture (GM) on Lie Groups, Object SLAM with symmetric objects
* Gaussian Mixture can be used to model multiple hypothesis
* How to define GM on Lie Groups? Proposes to use the midway point technique
* We note $X \in G$ an element in a Lie Group
* Gaussian distribution on Lie Groups: $X = \exp(-\xi^\wedge)\hat{X}$ with $\hat{X}$ the mean and $\xi \sim N(0,P)$, we note it $X \sim N_G(\hat{X}, P)$
* GM on lie Group: $\sum w_i N_G(\hat{X}_i, P_i)$ with $\sum w_i = 1$

Gaussian Mixture Merge:

* IV - A : Express a given Gaussian mixture distribution N_G(\hat{X}_i, P_i) but in the lie algebra of a common point $\hat{X}_c$
* IV - B : Compute a midway point $\hat{X}_f = (\hat{X}_2\hat{X}_1^{-1})^{w_2}\hat{X}_1$, express and merge the two gaussian distribution $X_1$ and $X_2$ on the Lie Algebra of the midway point 
* V : Numerical experiments with $SO(3)$ 

SLAM problem:

* promising example with SLAM with a symmetric object
* Impelement the Gaussian Mixture Invariant Extended Kalman Filter GM-IEKF