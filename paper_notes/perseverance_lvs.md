# The Lander Vision System for Mars 2020 Entry Descent and Landing

Authors: Andrew Johnson, Seth Aaron, Johnny Chang, Yang Cheng,
James Montgomery, Swati Mohan, Steven Schroeder,
Brent Tweddle, Nikolas Trawny and Jason Zheng

Year: 2019

Notes:
---
* Estimate position during mars EDL (entry descent landing) relative to a prior map (a map image, this requires robustness for landmark matching)
* Enables to approach hazardous sites 
* EKF for motion
* MRL (map relative localization) based on landmark fusion from frame to map with IMU fusion
* 40m error requirement
* Error analysis with Monte Carlo simulation

Commentaires:
---
Système intéressant, beaucoup de hardware, protocole de validation rigoureux. Mais un peu HS