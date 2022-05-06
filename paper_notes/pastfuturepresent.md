# Past, Present, and Future of Simultaneous Localization and Mapping: Toward the Robust-Perception Age

Author: Cesar Cadena

Year: 2016

Notes:
---

Introduction:
* Do robot need SLAM? Is SLAM solved?
* (1986-2004) = *classical age* with introduction of basic probabilistic formulations
* (2004-2015) = *algorithmic analysis age* study of observability, convergence and consistency, role of sparsity
* recent odometry have very low drift (<0.5 % of the trajectory) do we need slam?
* loop closure enables the robot to understand topology
* Vision based SLAM with slowly moving robots can be considered as a mature research field
* (2015-) = *robust perception age* self tuning capabilities, high level understanding, resource awareness

Anatomy:
* Posterior = belief over X given the measurements
* when there is no prior p(x) maximum a posteriori estimation becomes maximum likelihood estimation
* unlike Kalman, MAP formulation doesn't require a distinction between motion and measurement model but Kalman and MAP returns the same estimate in the linear Gaussian Case
* connectivity of the factor graph influences the sparsity of the SLAM problem
* the mismatch between filtering and MAP estimation gets smaller when the linearization point is good enough

Long term autonomy robustness:
* addressing failure modes for long term exploration
* bag of word address the problem of brute force matching on long term data association
* make the system failure aware? -> recovery mechanism with a tighter communication between front end and back end 
* for metric relocalization, using place recognition with a sensor (camera) but registration with another (lidar)
* automatic parameter tuning 

Long term autonomy scalability:
* design SLAM systems with memory complexity bounded
* sparsification (YEAH!) vs out of core algorithm (parrallel slam)
* continuous time trajectory estimation
* open pb: map representation (compressed known map), what can be forgotten?, severe computationnal constraint 

Metric map models:
* in 2D either occupancy grid or landmark based 
* TSDF *truncated signed distance function* space discretized into a set of voxels $v$ associated with $d(v)$ the distance of the 3D point on the nearest surface and a weight $w(v)$
* direct methods require GPU for RT
* how should we choose optimal representation? 

Semantic Map models:
* move from path planning to task planning 
* topological mapping: building a graph with distinguishable places
* SLAM helps semantic: use of monoSLAM to boost object detection in videos, 3D map for classification
* Semantic helps SLAM: use prior knowledge of object shape to improve the map
* joint SLAM and semantic inference
* semantic based reasonning, actionnability, levels of semantic... many concepts that comes with it 

New theoretical tools for SLAM
* factor graph optimization provides an elegant frame-
work which is more amenable to analysis
* Carlone show that 2D rotation estimation can be computed in closed form
* Carlone and Dellaert show that in most cases ML estimate is unique and pose graph can be solved globally via convex semidefinite programming
* computing a suitable initialization is also a good start
* theoretical work done on posegraph, can it be extended to other type of factor graphs?

Active SLAM:
* problem of controlling robots motion in order to minimize the uncertainty of its map representation and localisation