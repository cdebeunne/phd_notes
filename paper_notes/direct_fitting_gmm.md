# Direct Fitting of Gaussian Mixture Models

Authors: Keselman

Year: 2019

Notes:
---
* Usually model fitting with mesh is done by sampling points
* Propose to apprixomate the surface with a Gaussian Mixture Model (GMM)
* A GMM is a sum of a gaussian with normalization factors such that $\sum \lambda_i = 1$
$$
g(x)=\sum_{i=1}^K \lambda_i \mathcal{N}\left(x ; \mu_i, \Sigma_i\right)
$$
* How to get covariance of triangle? cf *Principal Component Analysis in CGAL* : use the vertices to compute a distribution centered on the center of mass
* Able to perform both P2D (point to distribution) and D2D registration
* Better than ICP on the stanford bunny (less outliers)
* Perform VO on the TUM dataset using D2D registration (more in *On-Manifold GMM Registration*)