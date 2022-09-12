# Real-Time Direct Dense Matching on Fisheye Images Using Plane-Sweeping Stereo

Author: Häne 

Year: 2014

Notes:
---

* adaptation of plane sweeping (R.T. Collins - 96) alg on fisheye images
* requirement: projection and unprojection done efficiently
* in comparison to the rectification approach, plane sweeping can be done on multiple images
* suitable for GPU implementations
* Use of unified projection model

### Stereo Matching on fisheye images

* Camera projection model $[u,v] = K D( h( \xi, X))$, $D$ to take distortions into account and $\xi$ is a scalar parameter that models the fisheye length
* Use a reference image $I_{ref}$ and a set of plane hypotheses $\Pi$ and each plane $\Pi_m$ defined by $[\mathbf{n}_m^T, d_m]$
* the planes are used as local reconstruction of the image => for each pixel of $I_{ref}$, the best plane is chosen
* For each plane hypothesis $\Pi_m$, the whole image $I_n$ is projected on the plane through a warped image $I_m$ and an image dissimilarity (ZNCC) is computed between each warped image $I_m$ and $I_{ref}$
* An aggregated cost is computed to take into account several views and motion
* Finally winner takes all strategy: the plane $\Pi_m$ with the lowest aggregated score is selected for each pixel
* subpixel interpolation for smoothness between neighbouring planes

### Commentaires

* Comment sont choisis les plans? Ne marche qu'en envirronnement structuré mais pourquoi pas