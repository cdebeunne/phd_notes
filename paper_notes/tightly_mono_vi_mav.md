# Tightly-Coupled Monocular Visual-Inertial Fusion for Autonomous Flight of Rotorcraft MAVs

Author: Shen

Year: 2015

Notes:
---
* superior size, weight, and power (SWaP) characteristics of a VINS setup
* first to demonstrate autonomous navigation with a VINS setup

## System
* Perform non linear optimization on a bunch of KF to estimate the gravity vector, all the robot states and the depth of the features
* all details in : Initialization-free monocular visual-inertial estimation with application to autonomous MAVs
* The bias are not estimated?
* Pre integration using quaternions
* Compute the covariance using the time derivative of the deltas 
* Information matrix of projection factors = FOCAL^2 * I
* Two way marginalization scheme: in hovering (vol stationnaire) the scale ambiguity may arise as keyframes are voted even with no motion to prevent from IMU divergence: marginalize the most recent state instead of the last in this case
* All the features that were first observed in a marginalized frame are also marginalized 

## Experiments
* 30 KF and 200 features in the sliding window
* 30 pixels of parallax (after rotation compensation ?) before being included in the sliding window
* Add KF every 0.1s
* Bias experimentally around 0 => not included in optimization

