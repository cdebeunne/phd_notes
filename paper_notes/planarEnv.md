# Motion And Structure from Motion in a Piecewise Planar Environment

Author: Faugeras

Year: 1988

Notes:
---

* camera is moving in a static environment
* for points in a same plane, the transformation is a homography
* We can get plane equation and motion from homography
* theorem:
$$
H_{12} = \alpha R + t n^T
$$
* 8 solutions to this equation according to the multiplicity of the singular values of H:
    * if 3 distinct values : 8 solutions
    * if 2 distinct values : 4 solutions
    * else it is undefined
* Degenerate cases: 
    * No translation
    * translation orthogonal to plane