# Suite

* the apical angle (see figure 3) is linked to the disparity on the epipolar rectified image by $\gamma_{\psi} = d / c$
* the depth is finally computed with the sin law and the baseline

### Stochastic observation model   

* approximates that accuracy of the pixel coordinates increases with $\phi$
* build an empirical stochastic variance model with orthogonal planes
* improve the stochastic variance model by:
$$
\Sigma_{ll} = \hat{\sigma}_1^2 I_2 + \hat{\sigma}_2^2 diag[\phi^{2p}]
$$
* the observation was the normal of three planes that are orthogonals: the orthogonality can be used to confirm the stochastic variance model

### Experimental validation

* for variance, use SGM and ELAS to produce dense PC on 30 stereo images and compute the 3 normal directions of the planes with RANSAC
* the residuals of each inliers of the 3 planes are computed to update the covariance factors $\hat{\sigma}_1$ and $\hat{\sigma}_2$
* $p$ is set to 8 as it matches better observations
* the orthogonality of planes is more precise with the improved stochastic model than with the classical one
* for $\phi > 40°$ the precision drops significantly
* ELAS and SGM performs similarly but ELAS slighly faster and more precise