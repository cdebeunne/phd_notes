# SLAM Course

Author: Joan Solà

Notes:
---
* Jerk = acceleration derivative
* Range = depth, bearing = direction
* K = Ks*Kf Ks: pixellisation matrix Kf: projection matrix
* Newton: D_x* = -H^-1 G^T
* Gauss Newton: least square of a vector function & D_x* = -J^+ e J^+ computed with Qr or Cholesky
* in GN H = J^t * J because the Hessian tensor is ignored 
* LMA add a line search to GN algorithm
* sparsity of the jacobian: each error depends on two states
* gimbal lock: pitch angle of +/- 90° => discontinuities on other angles
