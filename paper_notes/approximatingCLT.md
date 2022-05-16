# Approximating Discrete Probability Distributions with Dependence Trees

Author: Chow

Year: 1968

Notes:
---
* approximate n-dimensionnal distribution with a product of 2nd order or first order dependence with minimum difference in Information
* aproximate nth order into n-1 products of its distribution
* permissible approximations form:
$$
P_t(x) = \underset{0 < i < n+1}{\Pi} P(x_{m_i}| x_{m_{j(i)}}) 
$$
* Measure used to compare distributions:
$$
I(P, P_a) = \sum_x P(x) \log \frac{P(x)}{P_a(x)}
$$
* demonstration that shows that given our approximation, a solution that maximizes sum of MI minimizes I

Optimization procedure:
* construct a tree of maximal weight
* $\frac{n(n-1)}{2}$ edges in a graph with $n$ nodes
* we class the edges in increasing order, then build a tree from the highest to the lowest, discarding an edge each time in makes a cycle

Estimation:

* When the initial distribution is not known
    * uses the optimization with empirical values
    * uses ML estimator 