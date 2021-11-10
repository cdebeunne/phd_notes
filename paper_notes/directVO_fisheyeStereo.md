# Direct Visual Odometry for a Fisheye-Stereo Camera

Authors: Peidong Liu, Lionel Heng, Torsten Sattler, Andreas Geiger, and Marc Pollefeys

Year: 2017
___
Notes:
---
* Use of raw fisheye camera => study of the epipolar curve 
* One tracking thread (using only images of C_1) and one mapping thread (using both images)
* Tracking : aligning the current image on C_1 with the previous keyframe using photometric alignement (only with high gradient pixels) with a gauss newton algo and a Huber loss function 
* for fisheye stereo matching, using of the plane-sweeping stereo algorithm + multi depth hypothesis for each pixel
* the depth estimation is too hard to understand :o
* 1280x960 cam with a 50cm baseline (640x480 for real time perf)
___
Commentaires:
---
Stereo matching et estimation de la profondeur incompréhensibles... à revoir. Il faut peut être lire *Real-time direct dense matching on fisheye images using plane-sweeping stereo*

Le système est assez basique, pas de SLAM ni de filtrage 