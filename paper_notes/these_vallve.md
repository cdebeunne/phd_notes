<<<<<<< HEAD
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
=======
* demand computationnal time and ressources to store large matrices
* quadratic form of the NLS is only true around the optimal solution, and the Hessian is approximated with $2A^TA$ => may contribute to divergence of the step

Filtering:
* Bayes filters = the previous state is used to build a prediction (prior) and independant observations comes to reduce uncertainty
* prediction cheap but complexity of update step is $O(n^{2.37})$ due to matrix product
* Also exists information filter with information matrix and vector: there prediction is expensive but update cheap

Relaxation:
* idea: solve $\Lambda \Delta \mu = - \nu$ without inverting $\Lambda$
* Jacobi: decomposing $\Lambda = \Lambda_D + \Lambda_R$ between diagonal and non diagonal parts and iteratively compute the delta
* typo equation 2.34
* Gauss Seidel: similar to jacobi but $\Lambda$ decomposed between lower and strictly upper matrix

Line Search:
* idea: find $\alpha$ to get the optimal step $\Delta \mu = - \alpha H^{-1} \nabla$
* conjugate gradient takes $H$ conjugate directions instead of gradient, convergence speed depends on distribution of eigen values of $H$

Trust region:
* defines a region where the quadratic model is trusted
* LMA adds a radius term in the minimization cost: high damping = gradient descent, low damping = gauss newton
* Dogleg: polygonal path in 2 steps 

Discussion:
* Consensus as posing SLAM as a NLS problem
* relinearization is critical in terms of accuracy of solution
>>>>>>> 239ca2d74ed32a756f3b3021de4c0f049f240ff6
