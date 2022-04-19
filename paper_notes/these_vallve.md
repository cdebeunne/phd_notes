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

## III - Information theory

* basic idea: the less knon a topic is, the more information you can get, information = "resolution of uncertainty"
* self information: the information of an event $x$ is high if its probability is low $I(x) = \log \frac{1}{P(x)}$
* Entropy = expeted amount of information from an event we know its probability distribution, the more unpredictable an experiment is, the more entropy it has:
$$
H(X) = E[I(X)] = -\sum P(x_i) \log P(x_i) \\
H(X) = \log ( (2\pi e)^{n/2} |\Sigma|) \ \text{in multivariate gaussian case}

$$
* KLD describes how much a distribution probability differs from another: not symmetric, does not respect triangular inequality but positive and convex
* Mutual Information: measures how similar P(X,Y) is to P(x)P(Y) ie is the KLD between P(X,Y) and P(X) P(Y). For SLAM it gives how much a subset of variables injects information in another one

## IV - Information metric for Graph SLAM

* Goal: keep as much information as possible while growing the size of the pb
* sparsification = finding the best sparse and relinearizable approximation to the result of marginalization
* Pose SLAM only keeps new observations if their entropy is significant
* Markov Blanket = nodes at a distance 1 
* 2 phases of sparsification: building a topology (defining a new set of factors with measurements models $h_k(x)$) and factor recovery (computing $z_k$ and information $\Omega_k$)

Factor recovery:
* The new set of factors produces an approximated local distribution $q(x) \sim \mathcal{N}(\hat{\mu}, \hat{\Sigma} = \hat{\Lambda}^{-1})$ with $\hat{\Lambda} = \sum_k J_k^T \Omega_k J_k $
* We look for $\hat{z}_k$ and $\Omega_k$ that makes $q(x)$ the most similar to the dense local distribution before marg.
$$
\{\hat{z}_k, \Omega_k \}_{\forall k} = \argmin D_{KL}(p||q)
$$
* The solution in the Gaussian case:
$$
\hat{z}^*_k = h_k(\mu) \  \forall k \\
\hat{\Omega}^* = \argmin tr(\hat{J}^T \hat{\Omega} \hat{J} \Sigma) - \ln |\hat{J}^T \hat{\Omega} \hat{J}| \\
s.t. \hat{\Omega} \succ 0
$$
* For spanning tree topologies, $\hat{J}_k$ are invertibles, thus there is a closed for solution: $\Omega^* = (J_k \Sigma J_k^T)^{-1}$
* More complex topologies require iterative process like Interior Point (IP) or limited memory Projected Quasi Newton (PQN)
* Factor Descent (FD) is based on solving the problem in each factor subspace when the rest of the factors are fixed. For each factor, an analytical solution can be found
* TYPO: indices instead of indexes in factor descent algo
* Non cyclic FD: selecting the factor that will make the KLD decrease the most