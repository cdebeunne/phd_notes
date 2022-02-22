# ORB-SLAM3: An Accurate Open-Source Library for Visual, Visual-Inertial and Multi-Map SLAM

Author: Carlos Campos

Year: 2021

Notes:
---
* V, VI and multi map slam with pinhole, rgbd and fisheye lens model
* multi map used for relocalization
* Key of SLAM accuracy: long term data association
* improved place recognition by checking geometric consistency first and then local consistency
* Atlas = multi map system
* abstract camera representation => test new camera models :(
* Direct slam map estimation is reduced to pose map => less accuracy than sparse SLAM
* VINS Fusion KLT with shi tomasi kp
* ORB SLAM VI initialization too slow 

GREAT comparison between state of the art SLAM systems

Camera model:
* All properties and function depending on the camera model are extracted 
* MLPnp (maximum likelihood pnp) algorithm decoupled from the camera model => uses projective ray as input
* do not rely on stereo rectification => bo monocular stereo system

Visual Inertial SLAM:
* IMU pre integration on manifold
* Keyframe based VI SLAM
* huber loss not needed for inertial observations 
* Inertial initialization stated as a MAP estimatio problem of: the scale, the orientation of g, the bias and the velocity on 10 KF taken in 2 seconds
* *In some specific cases, when slow motion does not provide
good observability of the inertial parameters, initialization
may fail to converge to accurate solutions in just 15 seconds.*

Loop closing:
* DBOW2 can achieve 100% precision but 40% recall (=proportion d'items pertinents proposés sur l'ensemble d'items pertinents)
* Atlas system: active and matching map merging + loop closure with current KF and active map
* For each Loop closure hypohtesis, a local window of covisible KF on the candidate is selected to proceed to 3D alignement on a *matching map* and to validate or not the loop
* map merging operation: remove rendundant points between M_a and M_m, peroform local BA on the merged map with camera pose fixed and then pose graph optimization is performed
* loop closure = map merging but where both KF belong to active map