# A Survey on Terrain Traversability Analysis for Autonomous Ground Vehicles: Methods, Sensors, and Challenges

Author: Paulo V. K. Borges

Year: 2022

Notes:
---

## Intro:
* focuss on off road scenarios
* Chhaniyara et al., 2012 for planetary terrain analysis
* study camera, lidar or fusion of two solutions

## Taxonomy:
* obstacle detection -> occupancy maps (negative obstacle = holes)
* terrain classification: (grass, asphalt...) semantic
* traversability analysis: generate a "difficulty/cost map", depend on the type of robot
* model based method: based on explicit model e.g. sand is yellow pixels, robot cannot drive 20 degrees slopes
* data driven = learning methods (SVM = traditionnal learning vs. deep learning)
* proprioception may be used in terrain analysis: slippery terrain with wheel odometers, rugged terrain with vibrations observation (IMU)
* trav mettrics : terrain shape with roughness (small scale variation of the height of a surface) and slope using statistical analysis of 3D pc
* also metrics plateform dependant like kinematics and probabilistic metrics taking uncertainties into account
* difficult to define precise performance evaluation (except for classification) for unobservable metrics (difficulty), may be checking the configuration of the robot 

## Vision based methods:
* 3 classes : non learning methods, traditionnal learning methods and deep learning methods

non learning methods:
* stereovision method developped for MER mission
* terrain classification with color calibration and maximum likelihood estimator -> not robust to illumination changes and weather conditions
* disparity map computation -> elevation histogram
* (Bajracharya et al., 2013) stereo visual odometry + near field terrain map with classification and negative obstacle with voxel maps 
* negative obstacle detection is a challenge in night time with passive sensors 
* but their computationnal cost is predictable

traditionnal learning methods:
* extract feature point with descriptors (SURF or SIFT) and train a classifier (BOW, SVM ...)
* (Bajracharya et al., 2008) histogramm based naive bayes classifier with stereo range data
* near to far online learning method: near field stereo info (flat or not etc...) to deduce far-field terrain 
* In terrain classification DL > traditionnal learning methods (Shen and Kelly, 2017)

deep learning methods:

