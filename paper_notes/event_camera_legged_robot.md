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


### Sum Up

This paper deals with a visual odometry system based on both event and RGBD sensors. It is designed to address the issue of high dynamic motion produced by legged robots. The algorithm takes as input RGBD frames and an event stream that is turned into images. The authors propose to use Adaptive Time Surfaces (ATS), whose decay rate is dependent of the camera motion and the texture, as event frames. This is a direct method that uses a sparse selection of pixels on both RGB and event frames and performs image alignement to estimate the motion. The event pixels are selected using both ATS and event data, then filtered and sampled for more consistency. The pose is estimated with RGBD data only when the motion is smooth, and using RGBD and event data when the motion is highly dynamic. The system is evaluated on the MVSEC dataset and outperform state-of-the-art algorithms such as VINS-MONO and USLAM. Experimental data on a legged robot are also tested, and the proposed algorithm is able to provide pose even when the robot is bounding or performing a backflip. 

### Related work

The analysis of related works is provided in the introduction section of the paper. The context of the research is well justified and documented.Many references are highlighted concerning event-based methods and all the problematics tackled in the paper are documented. However, it lacks references concerning RGBD based SLAM (e.g. *KinectFusion: Real-Time Dense Surface Mapping and Tracking* (Newcombe) for a direct approach or *An Evaluation of the RGB-D SLAM System* (Endres) for an indirect approach) that is one of the sensor used in this study.

### Minor comments

* Abstract: "both public datasetS" no s to dataset, you worked only on one public dataset
* I, par 2: "[14]-[16] proposed" It is strange to start a sentence with a reference, you should use a passive form
* I, par 8: "direct-method-based" clumsy formulation, you can simply write direct
* II, A: there is an inconsistency between the description of the figure 3 and its caption. In the text the $n$ latest pixels are selected to compute the decay rate while in the caption $n$ pixels are selected before picking the 6 latest events
* II, B, eq3: What are i and j? You should reformulate or explain clearly in the text the distance between points condition
* II, D: Inconsistency in pose notations, sometimes it is bold, sometimes it is not
* II, D: "$\mathbf{T}_{i-1} - \mathbf{T}_{i-2} > threshold$" this notation is not rigourous for $SE(3)$ transformations, you should use \ominus and Logarithm for differences on manifolds
* II, D, eq4: the argument of the minimization is $\mathbf{T}_i$ but it should be $\mathbf{T}^{RGB}_i$
* II, D, eq4: inhomogeneous term, you substract pixel coordinates to grayscale values, you should write $z_p^j - I_{RGB}(\pi_{RGB}(\mathbf{T}^{RGB}_i M_p^j))$ in the sum for $e_j$ for instance
* II, D: the information matrices are introduced but we have no clues about how they are estimated
* II, D: "$\omega_2 in Eq.(4) is set BY zero." is set TO zero sounds better
* III: Inconsistency using with groundtruth: here it is "ground truth", in III A it is "ground-truth" and on the caption of fig. 6 it is "GroundTruth". You should choose a notation and stick to it.
* III, B: How is the groundtruth of your dataset generated? Optical tracker? 

### Conclusion

This paper introduces new event data processing techniques that are implemented in a direct pose estimator based on RGB-D and Event data. These novelties enable strong results on challenging datasets and outperform several state-of-the-art algorithms. This is the strength of the paper: impressive results that are well highlighted on the video by the way. However, the paper lacks clarity and rigour when it comes to technical explanations. It deserves proof reading and more work on notations. Otherwise, this paper denotes a strong research work that deserves to be presented at an international conference.