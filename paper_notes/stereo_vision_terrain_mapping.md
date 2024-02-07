# Stereo vision based terrain mapping for off-road autonomous navigation

Author: Rankin

Year: 2016

Notes:
---
* Binary obstacle detection vs traversability cost analysis
* 2D grid map = traversable, non traversable, unknwon
* 2,5D map = digital elevation map
* 3D map = voxel grid
* increasing baseline => increase accuracy of range data
* a new origin in map coordinates is set up for every frame so that it fits a global map
* 32 bits to store traversability information [elevation sign bit, ground cover (8bit), roughness (1bit), classification (2bit), object (2bit), traversability cost, confidence]
* the range uncertainty of stereo range data increases quadratically with range, the height uncertainty increases
linearly with range
* Terrain classification in both terrain space or image space 
* Fuse information to build a composite world map: enables to smooth out wrong information
* Multi resolution dense stereo: better modelisation of bushes that are smoothed out
* problem of water surface that lies below the ground

