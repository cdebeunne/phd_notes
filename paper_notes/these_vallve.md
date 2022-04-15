# Information Metrics for Localization and Mapping

Author: Joan Vallve

Year: 2017

## I- Introduction

* active SLAM = mapping + localization + path planning
* develop and formalize information-based formulations for soa SLAM
* develop information-based active SLAM

## II - SLAM

* ways of reps SLAM: Bayes Net, Factor Graph, Markov Random Field
* variable ordering comes from graph theory
* Cholesky factorization was initially proposed to solve geodesy
* filtering: only current state estimated, old observations marginalized in a prior of current state (prediction)
* $p(Z|x)$ can be easily formulated with measurements models
* information matrix $\Lambda = \Sigma^{-1}$ and $\eta = \Lambda \mu$
* MLE assume that $p(x)$ is a uniform pd, with conditionnal probability of measurements wrt to the state:
$$
\mu = \underset{x}{argmax} \ p(x|Z) \\
= \underset{x}{argmax} \ \frac{p(z_1,...,z_n|x)p(x)}{p(z_1,...,z_n)} \\
= \underset{x}{argmax} \ \Pi \ p(z_k|x)
$$
* after linearization we have $\Delta \mu^* = \underset{\Delta \mu}{argmin} || A \Delta \mu + r ||^2$ (1)
* Problem is highly non linear => initial guess is critical for convergence
* Imposing null derivative, the solution of the Gauss Newton step of (1) is:
$$
A^T A \Delta \mu^* = - A^T r \\
\Lambda \Delta \mu^* = - \nu
$$
* Cholesky: uses $\Lambda = R^T R$ with R then forward backward substitution:
$$
R^T y = - \nu \\
R \Delta \mu^* = y
$$
* Landmark based SLAM $\Lambda$ structure can be exploited as the part of the block matrix concerning landmarks is diagonal
* Square root Sam uses QR decomposition of A, lets note that $R$ from QR decomposition is the same as R from cholesky
* When adding a new state, the measurment $e_k$ is 0: it is not necessary to solve again
* With variable reordering algorithm like COLAMD
* Incremental Cholesky and QR to make it more optimal
* iSAM rebuilds the pb each n nodes, iSAM2 uses the bayes tree to relinearize and reorder the problem depending on how much the linearization point diverges from the estimate