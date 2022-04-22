# Nonlinear Graph Sparsification for SLAM

Author: Mazuran

Year: 2014

Notes:
---
* Inference on factor graph is equivalent to NLS optimization
* Formulation of the good optimization pb of marginalization and sparsification:
    * pb convex
    * conserve block structure 
    * general approach
    * local approach (only in markov blanket)
* demonstration of KLD being an instance of MAXDET problem, which makes it a convex problem
* optimzation based on limited memory Projected Quasi Newton (PQN):
    * adaptation of Proximal Quasi Newton to box constraints pb (case of KLD minimization)
    * define a set of variables that are too close to boundaries and fix them
    * define the Hessian block of free variables
    * take a projected Newton step
* Here the projection takes the closest positive definite matrix, in the case of symmetric matrices, there exists a closed form solution 
$$
P(X) = \underset{Y \succ 0}{\argmin} ||X-Y||_F^2 = V diag(max(0, \lambda_i)) V^T
$$

Application to 2D graph SLAM:
* assume that they know which node to remove
* steps of marginalization and sparsification:
    * extract Markov Blanket of a node
    * Optimize node to get a local linearization point
    * Marginalize the point using Schur Complement
    * Select a set of virtual measurments
    * Solve KLD
* If $\Omega$ is not invertible, it means that Markov Blanket lacks  a rigid transform edge to the World Frame => needs to project it on a subspace where it is invertible
* Select the Topology using Chow Liu Tree for the tree based approximation
* Chow Liu Tree + greedy heuristic for the subgraph based approximation

Experiments:
* Manhattan and Intel are full 2D datasets 
* Try 4 levels of node reduction
* what is "fill in" ? percentage of non zero elements?
