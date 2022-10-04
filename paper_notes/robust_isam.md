# Robust Incremental Smoothing and Mapping (riSAM)

Author: M.Kaess

Year: 2022

Notes:
---

* Robusify iSAM to handle eroneous data association
* robust back end optimizer based on graduated non convexity (GNC)
* data association is NP-hard (?)

### Related Work

* Exact methods (JCBB) are not suitable for RT
* Other methods try to find the maximum consensus set (PCM, RRR)
* M-estimator: applying a robust kernel that applies a sub quadratic cost
* GNC proposes to optimize this kernel
* additionnal variables that calssifies costs as inliers or outliers
* GNC seems to be the best for SLAM scenarios

### Methodology

* convexifying the problem with a robust parametrized cost fct $\rho ( r, \mu ) $ with $\mu$ controling the convexity degree: this is called "graduation"
* infinite growth kernel lead to a single optimum skewed by outlier while asymptotically constant kernels lead to many local optima: a small $\mu$ leads to a infinite growth kernel (convex) while big $\mu$ leads to a-constant kernel (non convex)
* Efficient GNC algorithm to optimize the kernel
* propose the Scale Invariant Graduated (SIG) kernel:
$$
\frac{1}{2} \frac{c^2 r^2} {c ^2 + (r)^{\mu}}
$$
* it is convex for $\mu < 0.5$ and non convex for $\mu > 0.5$, $c$ is the shape parameter
* Adapt iSAM2 update to graduated solving 
* GN leads to large update in the presence of outliers
* the only incrementalizable line search algorithm is Powell's Dogleg but it is incompatible with EGNC => developped an incremental Dog Leg line search suitable for EGNC
* Putting all this together => riSAM
* plus: quadratic cost for known inliers (like odom meas) and classify strong outliers and strong inliers to initialize better $\mu$

### Experiments 

* ATE wrt iSAM2 run with inliers only
* Manhattan dataset with outliers in lc meas