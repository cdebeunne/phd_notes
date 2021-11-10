# Semi-Dense Visual Odometry for a Monocular Camera

Authors: Jakob Engel, Jürgen Sturm, Daniel Cremers

Year: 2014
___

Notes: 
---
* depth of all pixels that have a significant gradient (not all pixels ie. semi dense)
* probabilistic depth map with Gaussian param
* First feature less real time monocular VO
* depth map propagated frame to frame & based on stereo matching of pixels

Stereo matching: we compute the disparity of a pixel (ie its horizontal displacement) which is related to its inverse depth https://en.wikipedia.org/wiki/Computer_stereo_vision

* Uncertainty aware stereo including: photometric error, disparity error and pixel to inverse depth ratio
* depth map regularized by averaging the depth of neighbouring pixels
* dense tracking by minimizing photometric error 

___

Commentaires:
---

Papier trés technique, on s'y perd. L'implémentation a l'air trés galère mais c'est hyper puissant :o Je suis fan 