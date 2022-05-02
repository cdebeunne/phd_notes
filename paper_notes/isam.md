# iSAM: Incremental Smoothing and Mapping

Author: Kaess

Year: 2008

Notes:
---
* smoothing information matrix is naturally sparse, but in filtering approaches it becomes dense because of marginalization
* periodic variable reordering for loops (?)
* fast algorithm for data association
* solution based on QR factorization
* iterative optimization avoids the problem arising from wrong linearization point
* QR factorization with givens rotation -> set to zeros all entries below diagonal, constructs the Q matrix
* number of givens rotation is independant of the length of the trajectory
* With loops, information matrix remains sparse but R becomes dense -> variable reordering with COLAMD
* Uses ML data association (better than NN as it takes uncertainties into account, but slower)
* The full covariance matrix is never calculated, marginals are obtained performing backsubstitution on R matrix

Commentaires:
* Equations trés claires 