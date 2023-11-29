# A New Visual Front-end Combining KLT with Descriptor Matching for Visual-inertial Odometry

Author: Wu

Year: 2023

Notes:
---

* Tightly coupled KLT and descriptor matching for indirect VIO. Test method on both filter based and optimization based algorithm. Use KLT and superpoint (CNN method for extraction)
* Tackles the pb of lost tracked that are rediscovered after
* complementary strength: tracker for small motion, descriptor for big
* run tracking and matching in parallel and perform validation
* SuperPoint: *Following the encoder, the architecture is split into two decoders, each designed to learn the weights of specific tasks: one for keypoint detection and
the other for descriptor computation*
* KLT module: forward / backward tracking
* Descriptor module: KNN algorithm with k = 2 + forward backward tracking
* Points that are succesfully tracked with both 
* Then perform RANSAC filtering with fundamental matrix