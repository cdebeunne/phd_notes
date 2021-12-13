# A tutorial on Newton methods for constrained trajectory optimization and relations to SLAM, Gaussian Process smoothing, optimal control, and probabilistic inference

Author: Toussaint

Year: 2016

Notes:
---
* General discussion on Newton methods accros different disciplines starting from Newton based path optimization
* Gaussian Process > B-spline for smoothness constraint
* k-order Markov assumption, ie un état dépend des k états avant lui
* inverse optimal control: computing path from control
* Newton step D_x = -H^-1*g

SQP:
* Taylor approx at 2nd order for cost, 1st order for equality and inequality constraint and a standard quadratic programing (QP) method is used to compute the optimal step delta*
* But in practice gradient and hessian are hard to compute (kinematics and dynamics of systems required)
* Standard in robotic

Augmented Lagragian:
* adding penalties when constraints are violated in the cost function
* penalties (squarred penalties) and Lagrange (linear penalties) parameters added to the problem
* Lagrange parameters updated at each step
* Fulfill KKT after one iteration on most cases
* Does not require QP method, only Newton method

In practice the step H*D_x = -g is solved with cholesky decomposition

* Under k-markov assumption hessian of AuLa cost function is banded symmetric of width 2(k+1)n-1
* Solving d = -A^-1 b with A banded symetric of width l and b of size m is O(ml²) => solving path optimization is linear in T, the length of the path
* acceleration = xt + xt+2 - 2xt+1
* Gauss Newton: case of a cost function as a sum of squarred, the hessian is aproximated as J^T * J that is always semi positive definite (H is ignored as it is close to singularity)
* The newton step is the covariant gradient of f(x) wrt to the metric H (cf paper for the def of a covariant)

B-splines:
* for basis splines, gives a parmetrization of size k x(t) = b(t)^T*z
* for general path, x = Bz + b^Tx_0 ie linear representation of paths
* permits to optimize on lower dimension space BUT does not improve Newton algorithm, it just imposes smoothness to solution

GP prior & covariance regularisation:
* popular kernel is k(t,s) = exp{−(t −s)²/σ²} => breaks the k order markov assumption
* we can define a covariance regularised pb by adding x^TK^-1x term
* the hessian is thus H + K^-1

Commentaires:
---
Tuto très clair et notations assez explicites, lire la partie sur le controle optimal la prochaine fois

