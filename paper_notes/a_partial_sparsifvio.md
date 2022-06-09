# A Partial Sparsification Scheme for Visual-Inertial Odometry

Author: Wang

Year: 2020

Notes:

* here the dense prior on robot pose is kept, while the dense prior on landmark only is sparsified: recover only landmark-to-pose pseudo factors
* marginalization can cause inacuraccy as the linearization point of the prior is fixed
* when a KF is marginalized:
    * the pose, velocity and biases are marginalized into a dense prior H_d as in OKVIS & co
    * the landmark only connected to the KF are marginalized into another dense prior H_o that will be partially sparsified
* Uses NFR to sparsify H_o (is J really invertible?)

Results:
* Way faster than MKaess solution