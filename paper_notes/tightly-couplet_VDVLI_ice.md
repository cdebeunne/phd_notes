# Tightly-coupled Visual-DVL-Inertial Odometry for Robot-based Ice-water Boundary Exploration

Author: Zhao

Year: 2023

Notes:
---
* Multi State Constraint Kalman Filter (MSCKF) with vision, DVL, IMU and pressure
* DVL aided feature enhancement + marginalization scheme that leads to best performances
* optimization based VIO allow relinearization, not filtering 
* classic IMU update model
* DVL velocity measurement update, function of both angular and linear velocity:
$$

\mathbf{z}_{D, k}=h_D\left(\mathbf{x}_k\right)+\mathbf{n}_D={ }_D^I \mathbf{R}^{\top}\left({ }_G^{I_k} \mathbf{R}^G \mathbf{v}_{I_k}+\left\lfloor{ }^{I_k} \boldsymbol{\omega}\right\rfloor \times{ }_{\times}^I \mathbf{p}_D\right)+\mathbf{n}_D

$$
* Pressure measurement update function of z coordinates:
$$
z_{p_z, k}=h_{p_z}\left(\mathbf{x}_k\right)+n_P=\mathbf{s}_G^{I_k} \mathbf{R}^{\top}{ }_D^I \mathbf{R}_P^D \mathbf{R}\left({ }^P \mathbf{P}_{i n}-{ }^P \mathbf{P}_k\right)+n_{p_z}
$$
* Perform left nullspace of the visual features jacobians so that they don't include landmarks in their vector space
* Use only 2 feature measurement for visual update to save computational cost
* Need to marginalze two frames at a time (because marginalizing a visual measurement will bring no info if the lmks are not included in the state) cf. *Robust Stereo Visual Inertial Odometry for Fast
Autonomous Flight*
* aid triangulation of features using the sparse points of the DVL :
    * first interpolate the pose at the DVL timestamp
    * remove outliers of the DVL PC and put it in global frame
    * check if the feature is inside the DVL point cloud
    * perform bilinear interpolation of the feature depth
* Field exp under ice
* KLT + FAST > descriptor based method
* generates simulated data with openVINS (?)
* visual measurement noise of 0.09 (wtf again)