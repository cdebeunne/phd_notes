# Generic Factor-Based Node Marginalization and Edge Sparsification for Pose-Graph SLAM

Author: Bianco

Year: 2013

Notes:
---

* sparse approximation of marginalization using chow liu tree
* computationnal complexity depends only on the number of nodes removed, not on the size of the whole graph
* pairwise measurement composition != marginalization: some of the composed measurements share common information, ie. are not independant 
* interesting notations for marginalization
* GLC factor = unique factor to represent marginalization **over the elimination clique**
* marginalization induces n nary factors -> explicitly shows the correlation between measurements 
* the target information matrix $\Lambda_t$ may not be full rank 
* idea: builds a n nary factor with the pseudo inverse of $\Lambda_t$
* adapt it to relative frame by setting the first pose as an arbitrary origin -> ensure that the jacobians are invertibles
* CLT = maximum spanning tree over all possible pairwise information

Build CLT over $\Lambda_t$:
* take joint marginal $p(x_i, x_j)$ (how? with $\Lambda_t$ inversion apparently SCHUR COMPLEMENT)
* as CLT only need to sort mutual information, the absolute value doesn't matter -> Tikhonov regularization is ok
* A CLT approximation has a complexity of $\mathcal{O}(m^2 log \ m)$
* how to compute every spanning tree? 

Conclusion:
* GLC can represent either dense marginalization, either sparse CLT 
* superior in term of KLD than pairwise measurement composition