# Exploring Event Camera-based Odometry for Planetary Robots

Year: 2022

Author: Scaramuzza

Notes:
---
* event based camera for future helicopter mars mission 
* event: 1MHz rate, enable  operation in high dynamic range, low light
* estimation backend must deal with depth uncertainty because of hoovering and rotation only scenarios  => filter based approach are better suited => EKF solution 
* FAST/KLT tracking is optimized for frame inputs -> suboptimal for event based cameras
* state vector: sliding window of M camera poses + N SLAM features parametrized with anchor 2D pose and inverse depth
* EKLT:
    * tracks Harris corners
    * optimise warping and flow on an aggregation of event in a patch
    * synchronize evry time 3200 events are triggered
    * outlier rejection with residual thresh
* Limitation in computationnal performance: it is not real time capable 
* In cave scenario, just non divergence is shown

Commentaires:
---
Papier assez décevant, il reste du boulot à faire