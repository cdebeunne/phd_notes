# Pyramidal Implementation of the Lucas Kanade Feature Tracker Description of the algorithm

Author: Jean-Yves Bouguet

Year: 2001

Notes:
---

* Optical flow problem to solve ie. fine d that minimzes e(u) = sum_x sum_y (I(x,y) - J(x+d_x, y+d_y)) at a pixel u (the sum is in the neighborhood of u)
* pyramid representation I_m .. I_0 (usually 2,3,4 max) with u_l = u/2^L
* Find the optical flow at level L and use it as initial guess for level L-1
* Iterative Lucas-Kanade is a gradient descent of e 
* Bilinear interpolation for subpixel computation
* Handling features at the borders by redifining the neighborhood
* Define pixels easy to track according to the gradient computation of their error (that requires a G matrix easily invertible): These pixels are basically corners

Commentaires:
---
Papier classique de traitement d'image, juste des maths, à l'ancienne ahah