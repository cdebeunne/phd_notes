# High-Performance and Tunable Stereo Reconstruction

Author: Pillai 

Year: 2016

Notes:
---
* reconstruction with stereo at 120 Hz with a stereo accuracy as input
* Semi Global Matching & ELAS = soa in stereo matching
* Only fpga or parallel processor based methods can reach rt
* DDPTAM: dense mapping from piecewise planar surface with PTAM

## Iterative stereo algorithm
* First step: construct a piece-wise planar scene with FAST features matched along epipolar lines, and Delaunnay triangulation
* It provides a depth prior for the second step: disparity interpolation of every pixel using the plane equation of every triangle 
* Third step: compute a census (5x5 patch) matching cost of the interpolated disparity
* Fourth step: determine costs of region high and low matching confidence and keep the disparity with the lowest cost in the disparity map
* Fifth step: support ressampling, region with high matching cost are resampled and the keypoints are mathced via epipolar search
* Then the process is performed iteratively 

## Experiments
* Evaluate against line sweep, SGBM and ELAS