# Real-Time Wide-Baseline Place Recognition Using Depth Completion

Author: Maffra

Year: 2019

Notes:
---
* VPR aided via depth completion from sparse local map
* proposes an alternative to feature based (inacurate) or CNN based method (too costly)
* Improve traditionnal feature based place recognition by densifying the map with depth completion
* Use BOW to detect loop and perform geometric check with denser 3D maps
* use a covisibility graph for a first filtering step: a query must be consistent with at least 3 covisible images
* Pb: with wide baselines, some loops will not share enough 3D landmark observations to perform pnp. 
* Compute the depth of newly detected features with a local 3D mesh estimated via 2D delaunnay triangulation