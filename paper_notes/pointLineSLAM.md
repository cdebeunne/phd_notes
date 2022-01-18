# A New Visual Inertial Simultaneous Localization and Mapping (SLAM) Algorithm Based on Point and Line Features

Author: Zhang

Year: 2022

Notes:
---
* bilateral filtering -> surf extraction -> FLANN 
* comparison to PL-VIO visu-inertial method basde on point line features
* robust to illumination and blur
* point based perform hardly in low texture envi like corridors => add line features
* Line Segement Detector (LSD) adjusted to meet real time
* LKT doesn't work in env with light changes => FLANN

Contributions:
- adaptive line segment algorithm for line processing
- bilateral matching 
- visual inertial initialization

Front end:

* adaptive filtering: blurs areas without texture, enhances edges  
* point -> surf -> flann -> KD tree for outliers
* line -> LSD -> geometric constraint for matching -> RANSAC
* FLANN: we take the smallest and the second smallest euclidean distance between features and if the ratio between the two is smaller than a thresh it is a match
* parameter tunning for LSD + a heuristic to determine if a segment is good
* geometrical constraint to match lines : lines are matched if they minimize angle, length ration, projection ratio and midpoint flow (procédé intéressant pour prendre en compte différents critères de matching)

IMU intialization:

* scale, bias and gravity vector are estimated on several KF
* bias are updated through time