# Error Propagations for Local Bundle Adjustment

Author : Lhuillier

Year : 2009

Notes:
---

* Local BA = sliding window BA
* required properties: uncertainty propagation + RT performance
* covariance approx by inverse of hessian (cf Multiple View Geometry) but doesn't exhibit propagation
* Work on measurement noise computation *Uncertainty ellipsoids calculations for complex 3d reconstructions* By Lhuillier
* Proposes four methods with either strong hypothesis (independance between state and measurements) or weak hypothesis
* Shape of uncertainty ellipsoid highly depends on gauge choice
* Unreadable equations