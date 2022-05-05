# Nonlinear Factor Recovery for Long-Term SLAM

Author: Mazuran

Year: 2015

Notes:
---
* method to recover best set of non linear factor (NFR) to represent marginal distribution
* 5 steps:
    * Markov Blanket extraction
    * Markov Blanket optimization (optional) : local linearization point or global 
    * Node marginalization with Schurr
    * Factor retrieval
* X is the inverse of the covariance of all measurement != I
$$
I = A^T X A
$$
with $A = \frac{\partial f}{\partial x}|_{x=\mu}$
* If we find X we have all our factors
* Closed form solution if A is invertible
* Efficiency of PQN strongly depends on initialization
* Why for SE(n) measurements, $\Omega$ is rank defficient? Because we are in the context of node removal with only relative transform
* Project information matrix on lower space where it is full rank

Topology:
* Chow liu tree is the sparsest
* Mutual information is undefined with under constrained pb => Tikhonov regularization $\Omega + \epsilon I$ 
* subgraph topology starts from chow liu tree and adds most informative edges
* Cliquey subgraph is the more dense that leads to closed from computation

Theory:
* Non optimality of error propagation wrt KLD (some dudes just fuse some succesive poses to reduce the amount of information)
* Show the equivalence between local linearization and global linearization

Experiments:
* use g2o (g2o uses sym gradient isam uses numeric gradient)