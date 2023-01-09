# 4Seasons: Benchmarking Visual SLAM and Long-Term Localization for Autonomous Driving in Challenging Conditions

Author: Wenzel & Cremers

Year: 2022

Notes:
---
* Benchmark with drastic appearance variations caused by seasonnal changes and huge variety of environments
* Used for VO, global place recognition and map-based localization
* 300 km of recordings with RTK GNSS gt, IMU and stereo images
* setup: homemade stero camera, 30cm baseline, camera and IMU triggered by FPGA
* Guarantee equal exposure time between left and right image and a smooth exposure transition
* Kalibr for calibration + Kannala Brandt model for cameras
* relative 6DoF GT with DSO and absolute GT with GNSS
