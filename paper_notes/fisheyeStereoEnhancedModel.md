# Direct Fisheye Stereo Correspondence Using Enhanced Unified Camera Model and Semi-Global Matching Algorithm

Author: Khomutenko

Year: 2018

Notes:
---
* Semi-Global matching alg well known for stereo corespondence
* omnidirectionnal LSD SLAM => curve sampling is way more computationnally expensive than searching on lines

Enhanced Unified Model:
* It is based on a projection surface (of revolution): the image point is obtained by scaling the 3D point on the surface and then projecting it orthogonally on the image plane (cf fig 1)
* For pinhole model, the projection surface is the plane z=1
* With the constraints of a projection surface, we can get the projection surface equation from the parameters of the model
* Then straight lines are projected as conic sections (the only straight lines projected as straight lines are those going through the optical center)
* Develop the equation of the conic section of a given line (that defines a plane with the optical axis) these are epipolar curves

Stereo matching:
* The stereo equation with essential matrix gives the equation of the plane => gives the conic equation 
* we get a polynomial with a dirty equation :/
* we need to rasterize the curve ie convert it into pixels (this is the expensive part)
* rasterization: start from a point (the epipole) and follow the curve thanks to the gradient until another point (the other epipole)

Semi Global matching algorithm:
* Require a table of photometric error for all pixels and disparity (if the disparity is evaluated on 64 level we need width x height x 64 of memory) here they use blocks of 3 x 3 pixels to reduce the memory needed 
* For every epipolar curve, a narrow band is computed around it and the average photometric error is computed on each block of the band 
* Dynamic programming: find a path in the error buffer that is optimal
* programmation dynamique = trouver une solution optimale en combinant des solutions optimales à des sous problèmes