# SLAM Course

Author: Joan Solà

Notes:
---
* Jerk = acceleration derivative
* Range = depth, bearing = direction
* K = Ks*Kf Ks: pixellisation matrix Kf: projection matrix
* Jacobian on manifold = J_i*M_i
* Newton: D_x* = -H^-1 G^T
* Gauss Newton: least square of a vector function & D_x* = -J^+ e J^+ computed with Qr or Cholesky
* in GN H = J^t * J because the Hessian tensor is ignored 
* LMA add a line search to GN algorithm
* lambda = damping factor of LMA (if small the step if governed by the hessian and if large the step is governed by gradient)
* sparsity of the jacobian: each error depends on two states
* gimbal lock: pitch angle of +/- 90° => discontinuities on other angles
* QR facto: Q is not computed explicitly, we use givens rotation to obtain R, use those rotations to transform A into a upper diagonal matrix
* Isam based on QR factorization, g20 on cholesky
* Cholesky HD_x* = -b -> R^tTD_x* = -b avec H = J^tOJ which is sparse
* => use of the COLAMD algo to get sparse R