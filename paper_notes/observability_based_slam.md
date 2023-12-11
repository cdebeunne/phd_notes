# Observability-based Rules for Designing Consistent EKF SLAM Estimators

Author: Huang

Year: 2009

Notes:
---

* Use a one landmark SLAM for example
* The choice of linearization points affects the observability of the EKF SLAM
* R = subscript for robot, L = subscript for landmark
* similar results with M landmarks or a single landmark: global translation and orientation are unobservables
* for an Ideal SLAM (using jacobian of real state values) the observation matrix is of rank 2 while it is rank 3 using the current estimates jacobians
* Using only the first estimate jacobians (FEJ) enables to have a proper observability of rank 3 (but introduces linearization error)
