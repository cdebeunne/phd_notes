# MegBA: A High-Performance and Distributed Library for Large-Scale Bundle Adjustment

Author: Jie Ren

Year: 2021

Notes:
---
* Existing libraries do not accelerate BA with GPU, do not provide distributed BA
* Uses JetVector to enable parallelism on every matrix operation
* Exact distributed BA
* DeepLM = distributed BA but uses pyTorch which is not optimal for memory gestion
* GPB interesting on IPU but IPUs are not widely available 

Principle:

* GN H = $J^T \Sigma J$, LM $H = J^T \Sigma J + \lambda I$ 
* Hessian is often stored as compressed Sparse Row (CSR)
* QR and Cholesky method suffer from $O(n^3)$ complexity => not cool for large scale BA

Design:

1) Solving sub BA pb in each GPU

For each sub pb 

2) compute Jacobians with JetVectors
3) construct approximated Hessian and gradient 
4) Apply PCG to compute the update
5) iterations until convergence

SIMD:
* requires to vectorised every operations, and implement input state and output in a SIMD manner with JetVectors
* Compute autodiff with Jetvectors
* Vectorized PCG to compute the step (not clear...)

Distributed BA:
* Method to divide into BA subproblem coupled to a method that synchronizes the states  
* subproblems are made of matrices that contains way less non zero elements 
* Some parts of the schur decompostion are synchronized between sub pb

Results:
* 3s with 8 GPU instead of 100s with ceres and 64 cores to build venice
* comparison by using double instead of float
 
Limitations:
* Only with NVIDIA GPUs
* Analytical diff not available 
