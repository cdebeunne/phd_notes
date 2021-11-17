# Vision-Based Navigation for the NASA Mars Helicopter

Authors: David S. Bayard, Dylan T. Conway, Roland Brockers, Jeff Delaune, Larry Matthies,
Håvard, F. Grip, k Gene Merewether, Travis Brown, A. Miguel San Martin

Year: 2019

Notes:
---
* Sensors: IMU, Lidar Altimeter, monochrome camera pointing at nadir
* Hardware: Navigation processor, Flight computer and sensors communicating with a FPGA interface
* Using pre mapped landmarks makes the vehicle pose become full observable (?)
* 90s flight on Mars => enables using velocimetry without too much drift
* Maven = minimal augmened state algorithm for vision based navigation EKF
* Only gyro data for landing because of dust

Algorithm description:

* 21 states (p_S, v_S, q_S, b_a, b_g, p_B, q_B) in a EKF
* p_B and q_B are clones of p_S and q_S used for updating EKF with two succesive images: First we identify a base image, then we update EKF with a search image and load the new pose p_S, q_S. When the number of matched features drops below a thr we set a new base image
* This methhod enables stable hover flight (vol stationnaire)
* At each measurement we have z_i and h_i(p_s, q_s, p_b, q_b) that can update EKF
* Filter tuning to increase camera and lidar weight for altitude estimation
* RANSAC prevents from lockout pb because it is not dependant of the current state

Vision processing:

* Use FAST corner detector with r = 5px range = 0.05
* Non maximum suppression to select good features
* Feature tracking with Kanade-Lucas-Tomasi (KLT) in a pyramid fashion
* Homography based RANSAC for outliers rejection (Homography is the transformation between two pixels of a same features taken from 2 different point of view) element from the same plane must have the same homography
* A small number of frames between base images help to guarantee the locally planar assumption, a threshold is set to 10 frames max
* De-rotation step with gyros to assist KLT (that needs a small diplacement to track features)
* Navigation and vision processing run at frame rate but it is a simple odometry 

Results: A lot of drift after 200s of flight