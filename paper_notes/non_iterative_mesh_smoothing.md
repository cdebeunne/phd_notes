# Non-Iterative, Feature-Preserving Mesh Smoothing

Author: Jones

Year: 2003

Notes:
---

* Mesh Smoothing algorithm applicable to every "triangle soup" with robust statistics
* pb: remove noise while preserving the shape
* previous work: isotropic algorithm (smooth salient features), diffusion equations (significant computationnal time), diffusion on normal field (same as before)
* capture the smoothness of a surface with local first order predictors

Method
---
* predict the surface of a triangle $q$ with a tangent plane $\Pi_q$
* estimate the position of a vertex $p$ based on the predictions $\Pi_q(p)$
* the estimate of a point is then the weighted average of all the predictors of $q \in S$ $\Pi_q(p)$ on a given surface $S$
$$
p^{\prime}=\frac{1}{k(p)} \sum_{q \in S} \Pi_q(p) a_q f\left(\left\|c_q-p\right\|\right) g\left(\left\|\Pi_q(p)-p\right\|\right)
$$
with $k(p)$ the normalizing factor:
$$
k(p)=\sum_{q \in S} a_q f\left(\left\|c_q-p\right\|\right) g\left(\left\|\Pi_q(p)-p\right\|\right)
$$
* Then mollification (i.e. smoothing of the normals (with the same method as before ?))