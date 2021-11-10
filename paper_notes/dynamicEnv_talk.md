# Dynamic Environments in Least Squares SLAM
Cyril Stachniss

link : https://www.youtube.com/watch?v=vtnh9TExdOI&t=2833s
___
Notes:
---
* Gaussian distribution doesn't take outliers into account
* Huber loss is better, downweights large errors
* Adaptive loss function is even better, but depend on a alpha parameter
* Optimisation pipeline that alternates between alpha and whole state 
* impressive results on ICP with moving objects 
* Semantic maps on LiDAR data with the range image in a CNN
* SLAM with semantic ICP exploits semantic to remove or ignore moving objects