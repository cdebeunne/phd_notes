# Event Camera-based Visual Odometry for Dynamic Motion Tracking of a Legged Robot Using Adaptive Time Surface

Author: Zhu

## Notes:

### Abstract:
---
* *major*: prétentieux

### Intro (Contains Related Works):

* Common approach event: create images from event at a constant rate and use feature based method (indirect) or using pixel brightness of images to estimate pose (direct methods)
* *Fig 4*: should be closer
* Time surface (event to frame alg decaying some pixels based on timestamp) to mitigate limitations of event images
* Proposes Adaptive Time Surface (ATS): the decay rate depends on camera motion and env texture
* Filters keypoints based on ATS

### Pose Estimation Framework:

* Time surface map: the grayscale value of the image emphasizes on the most recent event data
$$
\mathcal{T}(\mathbf{x}, t)=255 \times \exp \left(-\frac{t-t_{\text {last }}(\mathbf{x})}{\tau(\mathbf{x})}\right)
$$
* What is T_i^RGB? Precise if it is a SE(3) pose
* $\tau(\mathbf{x})$ is the decay rate which is here based on the surroundings pixels
* It ensures that the decay is faster in highly texture or highly dynamic environments 
* Fig 4 very usefull!
* For RGB, uses same method as DSO for pixel selection
* For events, uses a filtering method rps on Fig 5
* *Eq 3*: the notation for the distance threshold between pixels is not clear, what do the indices mean in $u_i$ and $u_j$?
* KF voting based on the number of pixels tracked
* T_{i-1} - T_{i-2} is wrong, you should use the manifold notations like \ominus
* T_i is not in bold
* Why 8 and 13 in the error sum? 
* How are the information matrices computed? why p and q subindices are used, it depends on the pixel or the entire patch? this is confusing
* Is set TO zero*

### Evaluation
* How the extrinsic between the sensors was computed?
* Lack of content concerning the run time

## Review:

### Résumé

This paper deals with a visual odometry system based on both event and RGBD sensors. It is designed to address the issue of high dynamic motion produced by legged robots. The algorithm takes as input RGBD frames and an event stream that is turned into images. The authors propose to use Adaptive Time Surfaces (ATS), whose decay rate is dependent of the camera motion and the texture, as event frames. This is a direct method that uses a sparse selection of pixels on both RGB and event frames and performs image alignement to estimate the motion. The event pixels are selected using both ATS and event data, then filtered and sampled for more consistency. The pose is estimated with RGBD data only when the motion is smooth, and using RGBD and event data when the motion is highly dynamic. The system is evaluated on the MVSEC dataset and outperform state-of-the-art algorithms such as VINS-MONO and USLAM. Experimental data on a legged robot are also tested, and the proposed algorithm is able to provide pose even when the robot is bounding or performing a backflip. 

### Related work

The analysis of related works is provided in the introduction section of the paper. The context of the research is well justified and documented.Many references are highlighted concerning event-based methods and all the problematics tackled in the paper are documented. However, it lacks references concerning RGBD based SLAM (e.g. *KinectFusion: Real-Time Dense Surface Mapping and Tracking* (Newcombe) or *An Evaluation of the RGB-D SLAM System* (Endres)) that is one of the sensor used in this study.