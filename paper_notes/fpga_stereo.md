# Enabling Continuous Planetary Rover Navigation through FPGA Stereo and Visual Odometry

Authors: Thomas M. Howard, Arin Morfopoulos, Jack Morrison, Yoshiaki Kuwata, Carlos Villalpando, Larry Matthies,
and Michael McHenry

Year: 2012

Notes:
---
* MER = Mars Exploration Rover ie Opportunity and Spirit
* Perception algorithms on FPGA instead of CPU => low power
* Grid-based Estimation of Surface Traversability Applied to Local Terrain
(GESTALT)

Parallelization of tasks for FPGA implementation: 

* Image aquisition: capturing, downsampling, transmission and storage
* Stereo: image rectification, filtering, disparity
* Visual Odometry: identification and tracking of features
* Traversability: heatmap for path planning
* Path planning 

Describes acceleration of stereo and visual odometry

* Stereo: use a rectification table and return a complete disparity map (ie range info for each pixel)
* 4 steps of VO:  features detection, feature matching with SAD (cache loading of features for fast matching), RANSAC to get a large set of inliers and reprojection error minimization

Acceleration of GESTALT

* Input: robot pose (VO), point cloud (stereo)
* Convert the map in a square grid, uses statistics of pc in the grid cells (mean, variance) to get slope and roughness and deduce traversability
* Select the best path to follow after generating a set of candidates

IDEA: GESTALT on a global map is more efficient at each step

Commentaires:
---
Pas tout compris à la partie hardware, mais donne un bon exemple de la marche à suivre