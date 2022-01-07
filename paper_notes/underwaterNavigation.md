# Comparison of feature detection and outlier removal strategies in a mono visual odometry algorithm for underwater navigation

Author : Alessandro Bucci

Year : 2020

Notes:
---
* Underwater images requests high exposure time, low image aquisition rate => feature matching instead of feature tracking 
* pre processing with CLAHE

VIO:
* 2 matches per feature then filtering with the Lowe criterion
* And the outlier rejection is done with modified ICP or RANSAC or RANSAC+ICP
* The scale ambiguity is removed with the altimeter
* 25 feature matches is the minimum for VIO to work
* Estimate the transformation $T_{k/k-1}, T_{k/k-2}, T_{k/k-3}$ to add additional constraints on the pose graph
* UKF-based estimator with amixed kinematic-dynamic vehicle model, where only the longitudinal dynamics is taken into account (more details in *An unscented Kalman filter based navigation algorithm for autonomous underwater vehicles*)

Conclusion:
* ICP run time way higher than RANSAC and less precise