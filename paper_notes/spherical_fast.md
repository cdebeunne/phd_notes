# Spherical FAST Corner Detector

Author: Kitamura

Year: 2015

Notes:
---

* detect corner in discrete spherical images
* longitude, lattitude leads to strong distorsion 
* sphere representation = isotropic ie the shape of an object is independant of the cam orientation
* FAST detector never detects at image boundaries

### Discrete spherical image

* tessalation base is an icosahedron 
* SIF image for processing : 2D representation of 3D shape without projection and interpolation (*Spherical image format* - Li)
* SHarris is slow due to spherical gradient computation

### S FAST

* Uses an hexagonal region around the pixel to compute the score
* Uses only 4 pixels to vote for a non corner to speed up the process
* look up table to save relationship between SIF and discrete spherical image for every pixels

### Experiments

* able to detect very distorted corners 
* but way slower than FAST (maybe due to opencv implementation)