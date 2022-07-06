# SuperPoint: Self-Supervised Interest Point Detection and Description

Author: DeTone

Year: 2018

Notes:
---
* fully convolutional model computes jointly interest point and descriptor
* state of the art homography estimation against SIFT & ORB
* Training CNN with strong supervision of interest point is non trivial
* supposed to run at 70 FPS?
* Self supervision: interest point pre training on synthetic simple shapes 'Magic Point', 'Homographic adaptation' to generate pseudo gt points that leads to 'SuperPoint', then a subnetwork is trained to produce descriptors
* Input -> encoder and one interest point decoder that returns an image with a probability of "point-ness" + one descriptor decoder that return an H * W * D output with one descriptor per pixel
* Homographic adaptation: warp an image in N images, extract with magic point on the warp images and aggregate all the detected KP