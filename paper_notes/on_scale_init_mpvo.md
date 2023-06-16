# On Scale Initialization in Non-Overlapping Multi-Perspective Visual Odometry

Author: Wang

Year: 2017

Notes:
---

* VO and scale init for MPCs
* Scale unobservability with straight or Ackermann motions
* *Real-Time 6D Stereo
Visual Odometry with Non-Overlapping Fields of View* two independant VO
* In VO scenarios, the motion is not reliable enough to bootstrap MPC VO
* Init the scale and the depth of landmarks on several KF
* The error term is based on alignement of bearing vectors:
$$
^{c_i} T_{c_j} \lambda b_k^i \times b^j_k = 0 
$$
* Then perform sliding window BA 
