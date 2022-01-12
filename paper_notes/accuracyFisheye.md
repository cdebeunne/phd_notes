# Accuracy of fish-eye lens models

Author: Hughes

Year: 2010

Notes:
---
* Radial barrel distortion noticeable on fish eye lenses => resolution decrease on peripherical areas of the image 
* odd-order polynomial models cannot sufficiently compensate for radial distortion => alternative models studied here
* assumption : lens displacement curve (?) is linear near the foveal and is monotically increasing
* *Displacement curve* = describes the radial dusplacement of points from pinhole to fisheye plane given any radial value
* pinhole model preserves straightlines $r_u = f tan(\theta) $

projection models:
* equidistant $ r_d = f \theta $
* equisolid: length of the chord on the unit sphere $ r_d = 2f sin(\frac{\theta}{2} )$
* orthographic $ r_d = f sin(\theta) $ but suffer from strong distortion 
* stereographic $ r_d = 2f tan(\frac{\theta}{2})$ the center of reprojection is the oposite of the tangential point 
* PFET (polynomial Fisheye transform) $ r_d = P(r_u)$ 5th order is good
* FET (fish eye transform) $r_d = s ln(1+\lambda r_u)$
* FOV model $r_d = \frac{1}{\omega} arctan \left ( 2 r_u tan (\frac{\omega}{2})\right )$ with $\omega$ the FOV of the camera 
* radial distortion can model deviation from real model $\Delta r_d = P(r_u)$

Results:
* Most of fish eye lenses are supposed to fit with equidistant or equisolid projection model
* Init f = 2 / FOV and 0 for the radial distortion parameters

Commentaire:

Décrit précisément les modèles de lentille, top! Pas hyper bien compris la technique de calibration