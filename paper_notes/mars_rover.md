# Two Years of Visual Odometry on the Mars Exploration Rovers

Authors: Mark Maimone,
Yang Cheng, and Larry Matthies
___

Notes:
---
* 6DOF VO by tracking features between stereo images
* Impossible to use VO while driving "fast"
* Helps to estimate slip
* Tracks Harris features with the highest score and compute their 3D position with stereo vision
* Features tracked with the 3D position and odometers, remove outliers with ransac and a first motion estimation is performed
* Then the robot motion is refined with ML estimation
* cam  : 640x480px 80x64° and 8.4cm baseline 