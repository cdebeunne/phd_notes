# Direct Sparse Visual-Inertial Odometry using Dynamic Marginalization

Author: Stumberg / Cremers

Year: 2018

Notes:
---

* Visual Inertial odometry using photometric error on a sparse set of keypoints
* perform "partial marginalization" to marginalize variables with an unknown scale
* SOA on EUROC
* 2 threads
    * Coarse tracking thread that uses direct image alignement with inertial alignement
    * BA threads on the active KFs
* Photometric error: compare the image intensity of the reprojected landmark, with image illumination affine correction
* classic pre integration factor
* initialization of the monocular vio problem including gravity direction and scale in the global problem
* Discard variables that affects sparsity of the system + First marginalize all the landmarks before marginalizing the KF itself (More info in DSO paper)
* Dynamic marginalization: reset the marginalizaton prior when the scale estimate moves too far from the linearization point of the prior
* Uses three marginalization prior that includes more or less information through time and slide them (the oldest is discarded, the middle becomes the oldest and the current becomes the middle) when the scale changes too much