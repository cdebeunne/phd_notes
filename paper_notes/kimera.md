# Kimera: from classical SLAM to 3D spatial perception

Author: Antoni Rosinol

* Robot able to answer high level queries
* Kimera = metric / semantic SLAM with stereo images and IMU
* goal geometric + semantic accuracy
* first step: sparse odometry to generates 3D mesh
* Uses CNN for semantic
* 3D semantic mesh doesn't the concept of object => it is not actionnable 
* 3D dynamic scene graph: 
    * layer one: metric semantic mesh
    * layer two: objects and agents (detects and tracks agent like humans/objects)
    * layer three: places and structure (free spaces rps as topological map, ready to be used for path planning)
    * layer four: rooms
    * layer five: buildings
* How to optimize a 3D mesh? with pose graph optimization on each vertices
* Update 3D mesh is really hard

Futur of SLAM:
* learning in SLAM is loosely coupled => tightly coupling?
* idea compute gradient of weights wrt SLAM problem
* differentiable rendering for SLAM

Semantic = what a human can tel about of a pixel