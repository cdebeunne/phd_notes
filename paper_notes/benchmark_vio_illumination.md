# A Benchmark for Visual-Inertial Odometry Systems Employing Onboard Illumination

Author: Kasper

Year: 2019

Notes:
---

* 160 minutes of video/IMU with 1500/4500/9000 lumens
* start and end at the same position -> accumulated drift as a metric
* utility of LiDAR reduced in long hallways or tunnels
* light source violates brightness consistensy assumption made in most direct methods
* use a light model 
* vicalib for calibration of the sensor rig
* photometric calibration is provided
* uses SplineFusion to estimate temporal offset between each sensor and gt measurements
* captures of targets to produce light calibration
* basic calibration of light is given by
$$
I = \frac{\alpha L  \cos \theta}{d^2}
$$
* details of metric used for loop closure 
* OKVIS is the best, ORB SLAM failed under bad illumination conditions 

Commentaires:

* excellent papier dataset