# On the Accuracy of Dense Fisheye Stereo

Author: Johannes Schneider

Year: 2016

Notes:
---
* Analyse of an epipolar rectification model with existing dense methods
* 6-7Hz point cloud generation
* Use method of (Abraham and Förstner 2005) for image rectification
* Test Semi Global Matching (SGM) and Efficient large-scale stereo (ELAS)
* Rigorous variance estimation of the disparity

### ELAS
* generative probabilistic model for stereo matching 
* Bayesian approach that builds a prior over the disparity space with a set of triangulated points
* MAP to compute disparity on the epipolar line

### SGM
* Uses MI as the matching cost
* global cost function that penalizes small disparity steps
* considers 8 straight line paths considering symmetries in all direction (?)

### Dense Fisheye stereo
* Uses the equi distance model i.e. the same as us
* The rectification model projects the epipolar planes to the same image row in both images
* We note the ray of a pixel $[x_1, x_2, x_3]$, the rectified pixel $\mathbf{x}^*$ $has the following coordinates:
$$
\mathbf{x}^* = \begin{bmatrix} \text{atan2} \left ( x_1, \sqrt{x_2^2+x_3^2} \right ) \\
\text{atan2} (x_2, x_3)
\end{bmatrix}
$$
* propagation of uncertainty on rectified image with jacobians
* 3D point cloud using the apical angle
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