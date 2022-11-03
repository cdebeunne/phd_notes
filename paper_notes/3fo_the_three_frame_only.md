# 3FO: The Three-Frame-Only Approach for Fast and Accurate Monocular SLAM Initialization

Author: Zhang

Year: 2022

Notes:
---

* Init monocular slam using 3 frames => 5 times faster and 36.7% more accurate on ORBSLAM2 w/ EUROC
* traditionnal: 2 frames and PnP + BA
* here: landmarks init on 2 first frames, third frames to filter outliers + MLP to solve essential matrix + BA
* MLP takes 5 points coresp as input and gives 10 depth estimations as output
* MLP is a classification network that returns *anchors*, the real depth is obtained with homotopy continuation