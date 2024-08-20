# MBRVO: A Blur Robust Visual Odometry Based on Motion Blurred Artifact Prior

Author: Zhang

Year: 2024

Notes:
---

* motion blur is caused by camera's movement during exposure time
* extracts "exposure trajectory" (motion direction of pixels) and use it as a prior for optical flow and pose estimation
* use a synthetic dataset for training with 230k images
* end to end VO avec un matching modle et un pose module
* estimate the exposure trajectory with motionNet
* improve a flowNet using the exposure trajectory estimated
* compute a weight based on the angle between optical flow and exposure direction to add in the cost volume used in flowNet (this cost volume is computed for every optical flow value in a search radius)
* compute a mask based on exposure trajectory to weight flow to pose network
* 98 hours to train motionNet / 36 for FlowNet and 113 for Pose Net
* rotationnal motion blur is usually consistent => no improvement brought in this case 