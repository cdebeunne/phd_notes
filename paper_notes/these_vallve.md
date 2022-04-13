## II - SLAM

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