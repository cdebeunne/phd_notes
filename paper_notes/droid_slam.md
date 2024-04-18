# DROID SLAM

Year: 2022

Author: Teed

Notes:
---

* Differentiable Recurrent Optimization-Inspired Design (DROID) = recurrent iterative update on depth and pose on an arbitrary number of frames (makes full SLAM with it)
* Combines direct (use the full image) and indirect (minimize reprojection error) methods
* Each image is represented by a pose and inverse depth of all pixels
* Use a frame graph based on overlapping FoV to handle loop closure detection
* Extract features with a network and perform correlation with overlapping images based on RAFT (an optical flow estimation alg)
* At each iteration: take an image, project every pixels on every overlapping image, use the correlation volume to retrive correlation feature, go through another network to buld a hidden state $h$ that is used to correct the correspondences, then perform dense BA on each correspondences 
* Train with a pose loss (GT vs predicted) and a flow loss (predicted flow vs flow predicted with GT)
* Front End: select KF and perform local BA
* Back End: global BA