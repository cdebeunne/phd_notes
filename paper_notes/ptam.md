# Parallel Tracking and Mapping for Small AR Workspaces

Author: Georg Klein

Year: 2007

Notes:
--
* design for AR applications
* tracking and mapping are split in two threads 
* big upgrade: no prior map
* constraints: scene must be small and static

Method:
* KF based ba for mapping
* map initialized with stereo pairs (5 point algorithm)
* thousands of points are mapped
* hand held context => hard to track, data association is hard
* Each KF stores the level of the pyramid of the image, a map contains points and KF
* Keypoints are patches with normal (which is not optimized)

Tracking:
* maintains a real time estimate of the camera pose relative to the map
-> map points are projected on the image
-> 50 coarse features matches on highest pyramid level
-> update of the camera pose with these matches
-> 1000 points are reprojected and matched
-> final pose is obtained with them
* FAST corner detector on each pyramid level
* measurement noise is the identity matrix (1 pixel)

Mapping:
* handles KF and points
* first initial map is built with stereo, then refined with KF from the tracking thread
* stereo map is made with RANSAC and two distinct images to determine fundamental matrix
* scale set by assuming 10cm between frames
* main plane is set to z=0
* KF voted if camera has moved (stationnary frames does not corrupt the map)
* new map points are initialized with 2 KF and with epipolar search and SSD
* local bundle adjustement is performed: 5 KF the last and the 4 nearest KF in the map + all the measurements of the points in the submap
* if the mapping thread is free (ie the cam in known area), data association refinement

Limitations:
* repeated structure makes the tracking hard: epipolar matching can match wrong patch

