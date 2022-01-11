# DM-VIO: Delayed Marginalization Visual-Inertial Odometry

Author: Lukas von Stumberg

Notes:
---
* Work on marginalization to limit the update time 
* scale is not observable with camera IMU in the constant velocity case
* initialization of gravity and scale with VIO in the beginning, then scale and gravity direction are still part of the optimization pb
* pose graph bundle adjustement with dynamically weighted photometric factors
* pre integration between KF of IMU data
* photometric strategy based on *DSO Direct Sparse Odometry*
* error dependent weight for photometric factors to reduce the weight of pixels with high error
* Marginalization with the Schur Complement 
* Marginalization creates a marginalization factor
* what is a active factor? a factor on active keyframes (maybe)
* Delays marginalization by Linearizing previous factors 
* Photometric factors shared between 8 KF 
* Marginalization is done step by step ie. once for each variable 
* Optimizing variables => obtaining covariance

Commentaire:

Papier très dur à comprendre, mais traite de l'utilisation des factor graph en temps réel: très intéressant. Le reprendre à tête reposée et/ou lire le papier DSO