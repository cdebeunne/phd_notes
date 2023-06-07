# Information Aided Navigation: A Review

Author: Daniel Engelsman

Notes:
---

* Review of of inertial navigation systems (INS)
* 3 aiding groups:
    * Direct aiding: knowledge about the carrying plateform (e.g)
    * Indirect aiding: external sensors 
    * model based aiding: fusion with vehicle model

## Direct Information aiding

* Zero Velocity in Navigation frame (SVN) while stationnary, it has the residuals $\delta \mathbf{z}_{\mathrm{zVN}}=\mathbf{v}_{\mathrm{INS}}^n-\mathbf{0}_{3 \times 1}$
* Zero velocity in body frame (ZVB): no slip assumption, the velocity perpendicular to forward direction are 0 $\delta \mathbf{z}_{\mathrm{zVB}}=\mathbf{v}_{\mathrm{INS}_{xy}}^b-\mathbf{0}_{2 \times 1}$
* Zero Angular rate in body frame (ZAR) angular rate is zero while stationnary. Good ref Brossard *RINS-W: Robust Inertial Navigation System on Wheels*
* cst altitude, zero down velocity, zero down acceleration, zero acceleration, constant llh position (slow motion that doesn't change latitude, longitude change), zero yaw rate, constant heading angle
* Virtual Lever-arm (VLA) : the lever arm is assumed to be a noisy value, it is added to the error vector

## Indirect information aiding