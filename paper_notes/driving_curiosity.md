# Driving Curiosity: Mars Rover Mobility Trends During the First Seven Years

Authors: Arturo Rankin, Mark Maimone, Jeffrey Biesiadecki, Nikunj Patel, Dan Levine, Olivier Toupet

Year: 2020

Notes:
---
* Review of MSL mission (exploring Gale crater and Mount Sharp)
* Curiosity = 6 wheels rover, that can rotate in both direction independantly (except middle wheels that are not steerable)
* Visual odometry enables SLIP estimates: evaluate the slip fraction by comparing the motion of VO with the one of wheel odometers
* Excessive SLIP may raise a fault or even stop the sol
* 99,55% of VO convergence

Categories of VO failure:

* Failed to converge (mostly due to a lack of features)
* Bug in step truncation (FSW is supposed to truncate large step to prevent from VO failure)
* Sequencing failure: Rover planners may send commands outside of the normal bounds
* Strategy filure
* IMU parameter failure 

Drives Modes:

* the whole VO process takes 47s on average
* Autonomous mode alternates between full VO (ie one iteration every meter) and slip checks (every 20 meters)
* Visual target tracking ie visual servoing. Tracking is performed with a correlation function cf *Overview of the Mars Exploration Rovers’
Autonomous Mobility and Vision Capabilities* (already available on MER)
* Path planning with D* algorithm
* Details of all drive failure cause (slip limits, time of the day exceeded, obstacle, tilt limit)
* TRCTL adapt each wheel speed to fit the topography: enables longevity of wheels and actuators

Commentaires:
---
Belle histoire, considération intéressante sur la mission et les causes d'échec. Mais HS pour la thèse