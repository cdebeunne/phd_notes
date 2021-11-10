# DeepFactors: Real-Time Probabilistic Dense Monocular SLAM

Authors : Jan Czarnowski , Tristan Laidlow , Ronald Clark , and Andrew J. Davison

Year: 2020
___
Notes:
---
* Learning a compact depth map representation (code c_i) with linear relation D_i  = D_i0 + J(I_i)c_i enables corelation between close pixels
* Three types of errors: photometric, reprojection and geometric. Included in a factor graph framework
* Inspired by CodeSLAM and CNN-SLAM. Refers to DeepTAM
* Using both learned and model based methods and both dense and sparse
* Depth map is learned with a supervised L1 loss + uncertainty parameter
* One way frames which are not keyframes but are used to refine the last kf
* pose based criteria for loop closure that adds additional pair wise constraints in the graph
___
Commentaires:
---
Encore un système hyper complexe, avec une nouvelle couche d'abstraction due au code... Implémentation de la depth map dans le factor graph très intéressante et compréhensible cependant.
