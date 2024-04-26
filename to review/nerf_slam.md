# Ternary-Type Opacity and Hybrid Odometry for RGB NeRF-SLAM

Notes:
---
* Include the prior of binary opacity into a Nerf with Ternary-Type (TT) opacity
* improve depth rendering => enables image warping odometry
* Nerf sLAM and Nicer SLAM uses pre trained depth net but not DIM SLAM
* Based on DIM SLAM
* Volume Rendering (VR) = generates images
* Eq 1,2,3 tel that the color and the depth is determine by the first 3D points encountered on the ray that has a opacity of 1
* DIM SLAM: multi resolution encoders to build feature vectors on grid maps decoders returns both density and color, then compute depth and color for each pixel. Scene representation and camera poses are jointly optimized on a set of frames w/ photometric loss, a warping loss (all the pixels are warped on another frame) to solve geometric ambiguities and a smoothness loss to deal with texture less regions
* $\eta$ is the initial value of $\phi_f$
* Super long paragraph about the necessity of dividing the set $S_0$ into $S_1$ and $S_2$, useless?
* softly binarized decoder $\phi_d$ with a softly binarized sigmoïd function
* Initialize the SLAM with $N_0$ first frames and use gt for the two first cam poses and use cst velocity model for the next ones
* hybrid odometry (combination of gradient based localization GL and BA)
* Group frames into set of $N$ frames: peform GL for each frame and BA for each set
* GL: take sample pixels from 5 previous frame and project it on current frame and minimize a photometric loss. Does not optimize $\phi_0$ and $\phi_c$ in this process
* keep a KF set based on a constant frame interval $H$ and select a subset $\hat{H_m}$ based on overlapping ration
* BA with photometric loss on the set of KF and the current group of frame: poses of the current group and feature grids are optimized there
* photometric loss: for each KF a random set of pixel is selected and the rgb value of rendered pixel is compared
* patch based warping loss: take patche on a frame and reproject it on every frame and compares its similarity
* Use 7 layers for multiset resolution
* evaluates on two datasets: replica and 7 scenes => better than DIM SLAM
* Ablation study of TT: enables reducing the number of BA iterations, tighter peak to compute the depth
* Ablation study of HO: logical, better accuracy

Remark:
---
* Figure 3 mentionned too late, needs to be later


Sum up:
---
This paper introduce a method to perform SLAM with NeRF with RGB data only. It is based on DIM-SLAM that doesn't require any pre trained depth or pose model but that suffers from a long training time. To improve DIM-SLAM, it is proposed to take into account the opacity property of surface by training the network to distinguish before, on and behind an obstacle. The theoretical insights are detailed before presenting the second imrovement: an hybrid Visual Odmetry. It consists in gradient based localization by warping for every image and bundle adjustement on a set of KeyFrames. For each image, the current pose is estimated with photometric error minimization on a sample of pixels without any rendering. For each KeyFrames, a photometric loss combined to a warping loss is minimized on set of pixels on rendered images. The proposed system outperforms DIMSLAM on most sequences of Replica and 7 scenes for both rendering and pose accuracy. Abaltion studies show that Ternary Type opacity improves the efficiency of BA while the hybrid odometry improves pose accuracy.

Related Work:
---
The paragraph about traditionnal VSLAM sums up well the field but I believe there are too many citations there. Citing one or two important paper and a review would be enough and some space would be saved for bigger figures or more qualitative examples. For the part about NeRF, the same remark can be applied. But it is good to be exhaustive in the part about SLAM based on NeRF and the dedicated paragraph is well documented. In the end, this paper denotes a solid bibliographic work but that needs a few less references, especially on the part that are not about the core of the paper (NeRF SLAM). I believe that 45 references is a bit too much for a conference paper that isn't a review. 

Minor remarks:
---

Abstract
* deploying THE Neural Radiance Field... the is useless here

Intro
* "Note that this process avoids the VR altogether during the tracking process, yet the camera poses are still refined via VR during BA." strange sentence that deals with two different things, should be reformulated
Ternary-type Opacity
* Table 1 is not necessary
* theorem 4.5: a proof is not necessary there
* theorem 4.6: in the proof the last sentence is a repetition
* theorem 4.8: what does it mean? what is the point of using the transport theory here, there is not any explanation except "it becomes clear". It is not to me

HO for Nerf SLAM
* why the depth of pixel $\times$ is $\mathcal{D}_x$, should be $\mathcal{D}({\times})$ as in section III
* Typo section V - B: eq (6), I would write it $X = R K^{-1} [x, 1]^T D_x + t$
* No information about the value of the number of pixels P in implementation details
* Again no info about R and L in implementation details
* Typo section V - C: represnets
* The set of patch size $Z$ is not discussed also
* Typo section VI - A: L_warping and L_rgb badly formated
* Sometimes TABLE is in caps lock or not, figure denoted by Fig. or Figure. Stick to one notation for both

Conclusion
* "[HO brings a] significant increase in overall speed" : in comparison to what? What would be the alternative to HO. You haven't compare the run time of your solution to DIM SLAM for instance. The only comparison was done on the number of iteration of BA, but it was not compared with and without HO

Major remark:
---
* The part IV was painful to read. I precise that I am not a specialist in machine learning. However, I find that these proofs are more based on intuitions than on rigourous demonstrations. That's why I believe that this format of theorem + proof is not suited for the message that is conveyed in this part. This could be summarized in a few sentences that highlight the intuition behind this ternary type opacity. It doesn't take two pages to explain that the set of opacity measures can be divided into two sets: one that needs to be optimized in front of the obstacle and the other one that can remain at the same value behind the obstacle. Reformulating this part would clearly enhance readability of the paper.

Conclusion:
---
This paper presents a novel SLAM system that uses a Ternary Type model to model a binary prior on opacity and that performs direct odometry based on depth rendering for tracking (called hybrid odometry). The overall method brings original novelties and the experimental section is well conducted with serious comparisons on two different datasets and ablation studies. However, the paper lacks readability. It needs a serious proof read and the section IV needs a complete reformulation. Moreover, an excessive number of citations and repetitions doesn't leave space for more pertinent informations such as: more implementation details, more qualitative figures and larger methodological figures.  