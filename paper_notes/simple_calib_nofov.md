# Simple Calibration of Non-overlapping Cameras with a Mirror

Author: Kumar

Year: 2008

Notes:
---

* Use planar mirrors to enable the camera network to see the same calibration target
* the 4 DoF of mirrors is introduced (3D normal vector $n$+ distance to camera $d$) as free parameters in the calibration process
* In the process, the cameras and the target remain fixed, only the mirror is moving
* each camera in front of a mirror is equivalent to a mirrored camera (fig2)
* the mirrored camera has striclty the same intrinsic and distortion parameters as the initial camera
* knowing the 4dof pose of the mirror, he derives an expression to obtain that links pose of the camera $C, R$ and the pose of a mirrored camera $C', R'$
* Augmenting the parameters to 15 to handle non linearity, this requires at least 5 mirror poses to compute $C, R$ in closed form
* Protocol :
    * The intrinsics and the mirrored camera poses are computed using a standard calibration toolbox
    * The camera poses are then computed using the $AX = B$ equation  
    * then a BA including the mirror parameters is performed