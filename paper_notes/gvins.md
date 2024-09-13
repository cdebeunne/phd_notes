# GVINS: Tightly Coupled GNSS–Visual–Inertial Fusion for Smooth and Consistent State Estimation

Author : Cao
Year : 2022

Notes:
---
* Fusion of VIO with GNSS pseudo-range and doppler shift measurements in a factor graph
* a quantity tought to be estimated is the 4 Dof transform between the local VIN frame and the global GNSS frame
* tight fusion
* GNSS - VI fusion with EKF : *UAV position and attitude
estimation using IMU, GNSS and camera* + *A robust
and modular multi-sensor fusion approach applied to MAV navigation*
* ECEF = earth centred, earth fixed $xy$ coincide with earth equatorial plane with $z$ pointing to the north and $x$ to the prime meridian
* ENU = semi global frame that is East, North and Up (gravity aligned)
* ECI = earth centred inertial frame: inertial coordinate system with center of mass of earth as origin and fixed wrt the stars (ie does not rotate with earth)
* Estimates a sliding window of poses and inverse depth, the yaw offset between local world frame and ENU frame, receiver clock bias and receiver drifting rate
* "pseudo" range cause contains  various errors
* Single Point Positionning (SPP) algo to perform trilateration in the ECI frame => four satellites needed
* INIT : 
    * classic Sfm for VI init
    * coarse anchor pose with SPP
    * yaw alignment with doppler meas
    * anchor refinement that imposes a clock constraint 
* Uses Doppler to find yaw: have a velocity estimate to align with VIO one
* Yaw offset cannot be estimated with low velocity 
* loop closure disabled for experiments