# Visualizing Spectral Bundle Adjustment Uncertainty

Author: Wilson

Year: 2022

Notes:
---
* Study eigen vector of covariance matrices of a BA = tangent space perturbation of the model
* *Camera uncertainty computation in
large 3D reconstruction* seems interesting
* *Fast and accurate camera covariance computation for large 3D reconstructions.* seems even better
* Discussion about $\Sigma_m$ (covariance of measurement), they choose $\Sigma_m = Diag(r(x))$
* Apply Schur Complement to get rid of 3D points parameters
* Discuss about defining a norm in $\mathfrak{se}(3)$ that is not trivial, normalize the error in translation and in rotation using the average error in translation and rotation (important to have a good visualization, this is not an issue for us)
* To avoid the inversion of the information matrix, they seek for the smallest eigenvectors of it (that should be the biggest of the cov)
* Vibrate each node (I don't understand this)
* This eigen value analysis doesn't allow to compare the accuracy of reconstructions     