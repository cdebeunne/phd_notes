# Invariant smoothing on Lie Groups

Author: Paul Chauchat

Year: 2018

Notes:
---
* group affine observation system = class of estimation pb on Lie Groups
* independence linearization => no need to relinearize 
* smoothing approach for SLAM takes advantage of the sparsity of the pb
* Here equations must have specific properties more than lying on manifold (group affine systems on Lie Groups)
* uncertainty on Lie-group with left or right multiplicative noise based on a gaussian noise vector projected through exponential map
* Extension to invariant KF to smoothing 

Smoothing:
* filtering: consider only latest state of the system
* smoothing: recover the MAP of the full trajectory given a set of measurements
* MAP can be converted in least square pb under the assumption of additive gaussian noise
* The link between factor graph is straight forward -> each term of the sum are referred as factors 
* $\boxminus : M \times M \rightarrow TM$ & $\boxplus : M \times TM \rightarrow M$ BEWARE these can be defined for left or right operation

Invariant smoothing:
* a group affine observation system has specific properties on $f$ (dynamic model) and $h$ (observation model)
* After calculations, linearization of factors do not depend on current state

Experiments:
* A 2D wheeled robot with odometers and artificial observations that are noisy added groundtruth poses (~GNSS) 
* All smoothing methods are more robust to wrong initialization than filtering  