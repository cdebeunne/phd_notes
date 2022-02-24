# g2o: A General Framework for Graph Optimization

Author: Wolfram Burgard

Year: 2011

Notes:
---
* BA and SLAM can be phrased as a least square optimization of an error function that can be represented by a graph
* set of measurements affected by Gaussian Noise 
* naive method like gradient descent, LM are not enough to achieve maximum performance
* similar to iSAM and \sqrt(SAM) but with improved performances

Least Squares:
* $e(x_i, x_j, z_{ij}) = e_{ij}$
* If a good guess $\check{x}$ you can use GN with a Taylor expansion that approximates the function
* $F_{ij}(\check{x} + \Delta x) = c_{ij} + 2 b_{ij} \Delta x + \Delta x^T H_{ij}  \Delta x$ with $b_{ij} = e_{ij}^T\Omega_{ij}J_{ij}, \  H_{ij} = J_{ij}^T \Omega_{ij} J_{ij} $
* The global problem can be solved by solving
$$
H \Delta x^* = -b
$$
* Update with $x^* = \check{x} + \Delta x^*$
* GN: iterates linearization, solving and update at each state
* LM: same with a dynamic damping factor at solving state:
$$
(H + \lambda I) \Delta x^* = -b
$$
* To avoid singularities, rotation are represented in over parametrized way like matrices or quaternion -> use minimal representation for $\Delta x$ -> $x_i^* = \check{x_i} \boxplus \Delta x_i^*$
* The jacobians become
$$
J_{ij} = \frac{\partial e_{ij} (\check{x_i} \boxplus \Delta x) }{\partial \Delta x}
$$
* sparse H matrix
* variable reordering + Schur complement for BA pb

Implementation:
* Use Eigen linear algebra package
* solvers for linear system: sparse Cholesky decomposition (does not take advantage of block decomposition of H) and preconjugate gradient 

Experiments:
* Analytic jacobians speed up from 80ms to 40ms on a given dataset
* faster convergence with se(3) parametrization
