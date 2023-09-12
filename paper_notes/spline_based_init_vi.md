# Spline-Based Initialization of Monocular Visual–Inertial State Estimators at High Altitude

Author: Liu

Year: 2017

Notes:
---
* poor init conditions with poor parallax or excessive integration period of IMU
* Ensures enough excitation of IMU to recover metric scale
* Vision and IMU have different criterias for proper init:
    * vision needs high parallax, not too dynamic motion
    * IMU needs agile motions (not constant velocity)
* Pb especially present at high altitude as high parallax needs long and constant velocity travel
* A B-spline is fitted on a up-to-scale VO trajectory to exctract derivatives of the trajectory, then the acceleration is aligned with the spline second derivative
* The method is also tested to bootstrap EKF and MSCKF
* Rotational components is substracted from images using EIS (electronic image stabilisation)
* states to be init: scale, gravity aligned attitude and velocity
* 6 order B spline to fit the traj
* write a joint problem formulation of both B-spline fitting and states alignement
* gyro bias are estimated in a stationnary position, they do not appear in the formulation
* Observability analysis of $b_a$ :
    * See the evolution of residual with perturbations on $\delta b_a$
    * Only with enough rotation bias and gravity can be destinguished
    * The bias are not incorporated in init