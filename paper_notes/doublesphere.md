# The Double Sphere Camera Model

Author: Cremers

Year: 2018

Notes:
---
* review of camera models for large FOV cam
* double sphere cam model (inexpensive and closed form inverse)
* assumption that all projections cross a single point
* pi^-1 unproject image coordinate to a ray
* for a pinhole cam model, fov is theoretically limited to 180° but in practice it can't go further 120°
* unified camera model (UCM) is used mainly with catadioptric cameras, five parameters $[ \gamma_x, \gamma_y, c_x, c_y, \alpha]$, if $\alpha = 0$ we have the pinhole model : first the point is projected on the unit sphere then onto the image plane with pinhole shifted by $\frac{\alpha}{\alpha-1}$
* extended UCM six parameters $[f_x, f_y,c_x,c_y,\alpha, \beta]$: the sphere of UCM is generalized to an ellipsoid
* Kannala Brandt camera model (KB): the distance to the optical center is proportionnal to a polynome of theta, unprojection requires to find the root of a polynome
* the difference between scaramuzza and Kannala Brandt is that Scaramuzza finds two polynomials: one for projection and one for reprojection
* FOV camera model: five parameters $[f_x, f_y, c_x, c_y, w]$ w is approx the FOV $r_d$ is computed wrt to $r_u$ and $w$
* double sphere (DS) : six parameters  $[f_x, f_y, c_x, c_y, \xi, \alpha]$ the point is consecutively projected on two unit spheres shifted by $\xi$ and then projected with pinhole on image plane shifted by $\frac{\alpha}{\alpha-1}$

Calibration:
* using a chess board with april tag markers to get 
* pb non convex => init important, intrinsics parameters with another method and initial pose with PnP alg
* FOV and KB are way slower than other methods