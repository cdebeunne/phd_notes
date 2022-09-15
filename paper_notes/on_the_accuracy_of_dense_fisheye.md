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