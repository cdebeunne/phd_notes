# Exploiting Uncertainty in Random Sample Consensus

Author: Rahul Raguram

Year: 2009

Notes:
---

* more robust esimtation algorithm, less iteration needed
* modified RANSAC with covariance check
* explicit characterization of the uncertainty of the model
* two closed form expression for covariance computation of both homography and essential matrix computation
* a covariance ellipse can be defined for the point transfert using the covariance of the homography and the one of the pixel
* Jacobian of SVD and fundamental matrix derived in *Computing the Uncertainty of the 8 Point
Algorithm for Fundamental Matrix Estimation*