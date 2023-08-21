Notes:
---
* Same pre integration measurement as in *Foster et al* but uncertainty is encoded in $SE_2(3)$
* Compare approaches by deriving IMU measurements on a KITTI trajectory by differentiating groundtruth
* $SE_2(3)$ is the most consistent approach according to the NEES criterion, while *Forster et al* approach degrades for long integration time
* Add random bias peturbation on measurements from KITTI, and it is more accurate for pose and velocity correction but similar for rotation