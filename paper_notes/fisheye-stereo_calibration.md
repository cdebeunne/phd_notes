# Fish-eye-stereo calibration and epipolar rectification

Author: Abraham

Year: 2005

Notes:
---

* method for generating epipolar images suitable for stereo processing
* two steps for stereo processing: calibration of the setup (intrinsic extrinsic) and rectification of the image pair
* classic fisheye model: mapping of the sphere to a plane then correction

### Camera model

* projection model is radial symmetric
* intrinsic model classical form with $r(\theta)$, principal distance and coordinates of the principal point
* distortion model set up with polynomials $\Delta x' (x', y') \Delta y' (x', y')  $

### Epipolar rectification

* generate a virtual stereo camera pair with no distortions, parallel optical axes and identical orientations
* epipolar planes are characterized by pitch angle $\beta$
* every image row must correspond to an epipolar plane 
* By noting with a subscript $v$ the values of the virtual camera and $\psi$ the yaw angle the rectification model is:

$$
x_v = f_{x,v} r_x (\psi) + c_{x,v} \ , \ y_v = f_{y,v} r_y (\beta) + c_{y,v}
$$
* for example the cylindrical rectification is given by 

$$
r_x (\psi) = \tan (\psi) \ , \ r_y(\beta) =  \beta
$$
* To get the value of the pixel $\mathbf{x}_v$, we come back to the original image like this:

$$
\mathbf{x}_c = \pi \left ( {}^c R_v \pi^{-1}(\mathbf{x}_v) \right )
$$
### Calibration and Experiments

* calibration software doing BA
* calculate Look Up Table for image rectification
* compare rectification with equi distant and stereoscopic models