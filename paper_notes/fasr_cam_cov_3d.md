# Fast and Accurate Camera Covariance Computation for Large 3D Reconstruction

Author: Polic

Year: 2018

Notes:
---
* Moore Penrose Pseudo inverse allow to compute the uncertainty of the the inner geometry and ignore infinity uncertainty of gauge freedom
* Propose a covariance matrix for the detection based on the "structure tensor" of the pixel (c.f Förstner, W.: Image Matching, vol. II, chap. 16, pp. 289–379. )
* propose a formulation of SfM that fixes the gauge with Lagrange Multipliers to avoid more penrose pseudo inverse to compute covariance
* Performs block inversion of the fisher information matrix to get uncertainty : use tricks to take into acount their gauge fixing method
* Application to very large Sfm problems