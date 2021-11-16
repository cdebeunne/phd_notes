# Two Years of Visual Odometry on the Mars Exploration Rovers

Authors: Mark Maimone,
Yang Cheng, and Larry Matthies

Year: 2007
___

Notes:
---
* 6DOF VO by tracking features between stereo images
* Impossible to use VO while driving "fast"
* Helps to estimate slip
* Tracks Harris features with the highest score and compute their 3D position with stereo vision
* Features tracked with the 3D position and odometers, perform a corelation based search for matching, remove outliers with ransac and a first motion estimation is performed
* Then the robot motion is refined with ML estimation
* cam  : 640x480px 80x64° and 8.4cm baseline 
* "update often, search less" doesn't work and other operationnal constraints
* IMU drifted slowly + good encoder based estimation
* VO used in high sloped : more features and risk to slip
* VO increased precision and safety of the navigation
* Navigating with rover track: slip check by looking backward 
* Slip checking device
* Necessity of wide angles camera for better feature tracking
___
Commentaires:
---
Bilan de deux ans de mission sur Mars: de belles anecdotes et une preuve de la nécessité de la navigation visuelle. Element de comparaison intéressant.