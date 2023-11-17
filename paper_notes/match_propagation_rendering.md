# Match Propagation for Image-Based Modeling and Rendering

Author: Maxime Lhuillier

Year: 2002

Notes:
---

* quasi-dense matching algorithm: starts with sparse sets of matches and propagates the neighbouring pixels
* IBMR (image base modeling and rendering) = 3D reconstruciton + rendering : the aim is to synthetize new views 
* Can be done with implicit 3D reconstruction with essential matrix or trifocal tensor
* "dense stereo algorithms are not sufficiently robust except
for precalibrated cameras in presettled environment "
* "sparse matching has been shown to be efficient due to its highly discriminant nature of the points of interest "
* extract GFTT and match them with ZNCC using cross consistency check (ZNCC > 0.8 w/ 11 * 11 windows)
* Then propagate each match in their spatial neighborhood starting with the matches with the best ZNCC score (best first strategy)
* Generalize the 1D disparity gradient limit to 2D i.e.  matched pixels must have matches in their surroundings with a similar 2D distance (use 5x5 neighbourhood for this check)
* perform a confidence measure to get rid of uniform areas
* Each time a new match is declared, it is added to the seed (avalanche behavior)
* The complexity of the algorithm is output dependant (i.e. it depends on the number of matched pixels)
* Avalanche behavior: needs a few seed matches
* Works well on low textured images: propagates along the lines