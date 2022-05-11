# C-KLAM: Constrained Keyframe-Based Localization and Mapping

Author: Nerurkar

Year: 2014

Notes:
---
* marginalize non KF information and maintains sparsity
* discarded =! marginalized
* both visual and inertial measurements
* Gauss Newton iterative has a complexity of $\mathcal{O}([K+N]^3)$ with $K$ the number of lmk and $N$ the number of robot poses
* exteroceptive measurements between non keypose and keypose destroy sparsity
* to maintain sparsity it ignores the data association between landmarks in keypose with non keypose
* approximated marginalization will only fill information with pose constraint between the consecutive keyposes
* computationnal complexity analysis of marginalization -> $\mathcal{O}(M_r^3)$ with $M_r$ the number of non key pose

Experiments:
* VIO with SIFT features matching 
* CKLAM takes 4% of the full BA time with 5% more error 