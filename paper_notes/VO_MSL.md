# Robust and Efficient Stereo Feature Tracking for Visual Odometry

Authors: Andrew E. Johnson, Steven B. Goldberg, Yang Cheng and Larry H. Matthies

Year: 2008

Notes:
---
* ICRA paper ie. contribution to CV community

Considerations about MER VO:
* MER VO uses spatial corelation with Pseudo Normalized Cross Corelation (PNC) + initial motion with gyro and odometers to match features between two frames (ie no descriptor)
* MER VO uses PNC as well for stereo matching
* Use an image pyramid strategy for PNC

To improve:
* Corelation search leads to large search windows 
* Too many features are rejected

MSL VO:
* Same stages as MER
* Pass through every stages at each level of the pyramid
* The bounding box for corelation search are smaller and smaller while going to the bottom of the pyramid: At each step, the bouding box for searching the matching feature is build on the previous motion estimation and the uncertainties on translation and rotation
* The covariance of the features is smaller as we go down the pyramid so that the search window becomes really small at the bottom
* Motion estimate with the left image only
* It works even with no prior on motion (eg if IMU and odometers crashes) by using the entire image at the top of the pyramid
* For the second stereo matching, the motion prior is used to define a search window on the right image
* LMS and ML as in MER motion estimator + tips for better numerical conditionning 
* Validity of a transformation by checking the eigen values of the scatter matrix A (??)

Performances way better than MER VO: faster and track more features

Implemented fully in C++

Commentaires:
---
Plein de petites astuces incroyables, papier très technique mais compréhensible en se concentrant bien

