# Attention and Anticipation in Fast Visual-Inertial Navigation

Author : Carlone

Year : 2017

Notes:
---

* Visual attention for VIN = selecting the best features
* find a subset S of features that maximises a function f(S) under the constraint $|S| < \kappa $
* F is built by anticipating the information matrix on a time horizon that takes into account the probability of loosing features
* reformulate a set of IMU measurements based on the prediction from the flight controller and compute an information matrix out of it
* a linear observation model is derived to predict the measurements of features and their information, the contribution of the landmark estimate is removed from the infromation matrix using the schur complement
* finding S* is np hard
* developp a greedy algorithm to find the best subset based on two $f$: one based on the minimum eigen value and one based on the log of the det