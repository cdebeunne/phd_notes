# SLAM for autonomous planetary rovers with global localization

Author: Dimitrios Geromichalos

Year: 2019

Notes:
---
* relative positionning via scan matching + global matching of local map to an orbiter global map
* Factor graph SLAM for planetary exploration : *Adaptive localization and mapping with application to planetary rovers*
* " However, LiDARs are hardly used in planetary rovers due to the heavy weight and high power consumption and to the authors knowledge , there exists no LiDAR sensor qualified for planetary missions. "
* No dense 3D reconstruction needed, just 2,5D elevation grid map

## GA SLAM

* for local mapping, scan to map with a particle filter combined with ICP
* for global pose, use template matching wrt orbital images

### Relative pose 
* PC are downsampled, transformed in the global map frame, cropped and the uncertainty of the eight of each point is computed using a sensor model
* Then update the local map (whose cells also have a 1D Gaussian distribution in z) using a Kalman Filtering operation
* Why map update is done before pose estimation?
* The scan matching particle filter estimates $[x, y,  \theta]$
* Use a particle filter where the weights of each particle is computed using the fitness score of a single ICP iteration
* The estimated pose is then the average of the particles with the highest weights

### Global matching
* template matching of local elevation map and global orbital map
* Uses the sobel operator to generate gradient images
* template matching cannot deal with rotated images: 20 rotated images are generated
* pose registration limited to the orbital view resolution
* the surroundings must be rich in elevation features

### Experiments
* data collected in tenerife
* a flying drone produced the DEM for the global map matching

