# ProSLAM: Graph SLAM from a Programmer’s Perspective

Authors: Dominik Schlegel, Mirco Colosi and Giorgio Grisetti

Year: 2017

Notes:
---
* Highlight algorithmic aspects of SLAM
* Stereo to simplify the pb: no scale drift and proper initialization of features
* Feature based method, landmark tracking (ie in the 3D space)
* Single threaded implementation for simplicity
* No bundle adjustment stage fo simplicity

Description of data structure:
* Keypoint *With Descriptor*
* Framepoint (bool inlier, 3D coordinates, track information, linked landmark)
* Frame (list of framepoints, cameras, pose and images)
* Landmark (pose in world, first, information matrix and vector)
* LocalMap (for fast relocalization) (pose, frames and landmarks)
* WorldMap (local maps, landmarks and posegraph)

Triangulation (raw image processing to frame with framepoints):
* Feature detection with FAST with automatic adjustement of the threshold
* Stereo matching with BRIEF descriptor and epipolar search on epipolar line (images rectified)
* Efficient search strategy by ordering kp in lexicographical orders of rows and cols

Motion estimation:
* Corespondences handle by the tracking unit
* Constant velocity model for transformation init (assumption valid with descent frame rate)
* The search for keypoint matching is performed in a rectangle around the init point and using the descriptor
* Pose is obtained by minimizing the projection error of the matched kpts

Map management (local maps):
* correspondence recovery with descriptors and unmatched kp
* new local map created according to transformation threshold
* information filter for landmark position refinement (?????)

Relocalization:
* Local Maps are relocalized to use richness of landmarks 
* This is done with similarity search on landmark's descriptor cloud with HBSR
* Then ICP is performed between lmks clouds
* a relocalization is validated if there is enough inliers in ICP
* then a link is added in the pose graph

Commentaires:
---
Super papier, très clair et système qui a l'air performant. Je vais peut-être dérober ce code hehe
