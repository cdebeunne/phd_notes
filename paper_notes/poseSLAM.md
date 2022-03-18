# Information-Based Compact Pose SLAM

Author : Ila

Year: 2010

Notes:
---
* Variant of SLAM with only the robot trajectory is estimated and where landmarks are only used to produce relative constraints between poses
* Only loop closure links and non redundant poses taken into account ie higly informative links
* Two measures: distance between two poses and mutual information gain 
* Leads to a more compact map
* Bottleneck for rt: data association that is solved with a tree based method
* Markov blanket of a node = all nodes linked or that are linked to this node
* difference made between observations linking two consecutive poses and observations linking other poses
* pose is redundant if it is too close to another pose already in the traj
* uses the formalism with information vector and information matrix this gives the following state update for a measurement $y_i^n$ linking states $i$ and $n$:
$$
\Delta \eta = H^T  \Sigma_y^{-1}(y_i^n - h(\mu_i, \mu_n) + H \mu_n ) \\
\Delta\Lambda = H^T \Sigma_y^{-1} H
$$
* mutual information gain = amount of uncertainty removed from the state 
* erf = error function linked to a gaussian (erf(z/sigma*sqrt(2)) = probability of a centered gaussian to have a value between -z and z)
* mutual information gain:
$$
I = \frac{1}{2} ln \frac{|\Lambda + \Delta \Lambda|}{|\Lambda|}
$$
* matrix manipulation to accelerate the computation of $I$
* bound pose similarity with interval arithmetic (ie. operations over intervals)
* pose tree to search for loop closure
* Very technical part about trees operations: recursive search & co

Experiments:
* real mapping with stereo vision, 3D landmarks and least square landmarks for pose estimation
* most of execution time due to nearest neighbour search