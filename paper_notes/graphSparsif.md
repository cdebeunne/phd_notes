# Graph SLAM sparsification with populated topologies using factor descent optimization

Author: Joan Vallvé

Year: 2018

Notes:
---
* reducing the graph, two steps: marginalization then sparsification with KLD minimization
* propose a KLD minimization without parameter tuning
* SLAM suffer from scalability: need to improve algorithm efficiency and reduce problem size
* For size: limiting the number of poses / select only observation with significant informations 
* Node marginalization = only solution to reduce the problem size without loss of info but we loose sparsity
* closed form solution of KLD minimization for simple graph topologies (ie spanning tree), for richer topologies, iterative optimization needed
* aim of sparsification: approximate the dense distribution returned by marginalization with a sparse distribution

Factor recovery:
* The mean remains equal so only the information matrix needs to be recovered with D_KL
* We seek for $\hat{\Lambda} = \hat{J}^T \hat{\Omega} \hat{J}$
$$
\hat{\Omega}^* = \underset{\hat{\Omega}}{argmin} \lang \hat{J}^T \hat{\Omega} \hat{J}, \Sigma \rang - ln |\hat{J}^T \hat{\Omega} \hat{J}|
$$

Factor Descent Algorithm:
* Solving at each step for a factor, fixing the rest
* proposition of null derivative computation
* topology = set of measurements
* positive definiteness enforced in the end of the FD
* non-cyclic factor descent: iterates on every factors in a decreasing order of the gradient of the KLD wrt $\hat{\Omega}_k$

Experiments:
* Home made SLAM on ceres
* Manhattan dataset = noisy pose graph

Questions:
---
* How do we choose the topology of our sparse graph distribution
