# Spherical Image Processing for Accurate Visual Odometry with Omnidirectional Cameras

Author: Hicham Hadj-Abdelkader

Year: 2008

Notes:
---

* perspective image tools are unable to handle geometrical distortion
* images are mapped onto a unit sphere and treated in the spherical spectral domain

### Intro:

* feature based: extracting features + matching and pose estimation (low accuracy but wide baselinge)
* template based: using the whole images (high accuracy but small baseline)
* Here uses feature based method to initialize template based method
* focus on feature based using Harris point detector and SIFT descriptor

### Background

* mapping of the image on the unit sphere:
    * sampling a equi angular grid on the unit sphere
    * spherical point mapped on the image plane with camera model
    * interpolation in the omnidirectionnal plane
* spherical spectral domain: $I$ can be expanded into a linear summation of spherical harmonic function
* convolution is defined in $SO(3)$ for spherical images

### Spherical image processing 

* gaussian filtering is usually performed before feature extraction => spherical gaussian filter
* Definition of spherical derivatives (w.r.t. $\theta$ and $\phi$)

### Feature based approach

* use spherical derivatives for Harris corners
* comparison using the repeatability rate 
* SIFT descriptors are built on a circular region in the spherical image
* Odometry using only $E$ estimation with RANSAC
* => improvement vs classical methods