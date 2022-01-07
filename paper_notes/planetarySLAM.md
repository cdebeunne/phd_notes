# Visual SLAM-Based Robotic Mapping Method for Planetary Construction

Author: Hong

Year: 2021

Notes:
---
* SLAM based method with stereo camera and deep learning based disparity map estimation
* Adaptation of S-PTAM, which is a stereo BA based SLAM
* Loop closure with BoW
* S-PTAM enables sparse mapping => necessity of a dense mapping method
* Self-supervised method for disparity map computation based on a SSIM loss
* Disparity map is also used to assist localization: is used to perform geometric check for loop closure and for feature matching procedure
* CNN run at 50Hz on a single GPU
* AKAZE used to extract and match features

Commentaires:
---
Papier intéressant, mais pas de contribution majeure. S'en inspirer pour mes travaux