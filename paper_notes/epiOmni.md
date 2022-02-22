# Estimation of omnidirectional camera model from epipolar geometry

Author: Micusik

Year: 2004

Notes:
---
* Calibration of a spherical camera model with automatic correspondences based on epipolar constraint 

Camera model:
* projection equation:
$$
\alpha g(Au' + t) = PX \\
\alpha \in \mathbb{R}, \ g(u,v) = (u, v, f(u,v))
$$
* non linear funtion $g$ compute 3D vectors with $f$ rotationnally symmetric wrt to $z$
* what is the digitized image?
$$
f(\mathbf{u},a,b) = \frac{r}{\tan(\frac{ar}{1+br^2})}
$$
* With model simplification calibration can be performed with 9 points RANSAC
* The model is linearized $p = as + bt$

Model estimation with epipolar constraint:
* constraint $p^T F p = 0$
* Leads to a QEP with concatenation of n points
* use the error between the ray and a epipolar plane (??) 
* u /= 1000 for better numerical stability


Commentaires:
---
Notations pourries, on s'y perd
