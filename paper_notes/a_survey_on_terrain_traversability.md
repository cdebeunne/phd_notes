# A Survey on Terrain Traversability Analysis for Autonomous Ground Vehicles: Methods, Sensors, and Challenges

Author: Paulo V. K. Borges

Year: 2022

Notes:
---

Intro:
* focuss on off road scenarios
* Chhaniyara et al., 2012 for planetary terrain analysis
* study camera, lidar or fusion of two solutions

Taxonomy:
* obstacle detection -> occupancy maps (negative obstacle = holes)
* terrain classification: (grass, asphalt...) semantic
* traversability analysis: generate a "difficulty/cost map", depend on the type of robot
* model based method: based on explicit model e.g. sand is yellow pixels, robot cannot drive 20 degrees slopes
* data driven = learning methods (SVM = traditionnal learning vs. deep learning)
* proprioception may be used in terrain analysis: slippery terrain with wheel odometers, rugged terrain with vibrations observation (IMU)
* trav mettrics : terrain shape with roughness (small scale variation of the height of a surface) and slope using statistical analysis of 3D pc
* also metrics plateform dependant like kinematics and probabilistic metrics taking uncertainties into account
* difficult to define precise performance evaluation (except for classification) for unobservable metrics (difficulty), may be checking the configuration of the robot 

Vision based methods:
