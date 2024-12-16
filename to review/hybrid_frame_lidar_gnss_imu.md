# Hybrid Frame-Enhanced LiDAR/GNSS/IMU Fusion System for Accurate and Robust Mapping

This text can be compiled as a markdown file.

## Sum up: 
This paper proposes a sensor fusion navigation pipeline relying on LiDAR / GNSS and IMU. 
It is based on a tightly coupled LiDAR / IMU state estimator that fuses IMU pre integrated residuals to feature based LiDAR residuals in a sliding window optimization scheme. 
This hybrid sliding window is made of a fixed number of consectutive frame $N$ plus a fixed number of keyframes $M$ that remain constant during optimization. 
The main contribution of the article is the selection of keyframes, based on the similarity of a Feature Matrix (FM) constructed with the edges and the planes extracted on each scan. 
The threshold of the similarity metric is adaptive, taking into account the amount of rotation in the current motion. Then, the estimated relative poses are incorporated in a global pose graph optimizer along with GNSS/IMU and loop closure constraints.
The variance of the edges from LiDAR/IMU odometry and from loop closure were empirically determined. This method was evaluated on a self collected dataset as well as trajectories from the Mulran dataset. 
To demonstrate the effectiveness of the keyframe selection method, an ablative study was performed and to demonstrate the robustness in degraded GNSS conditions an occlusion experiment was conducted. 

## Related Works: 
The author starts by introducing foundational works on LiDAR odometry and then provides an in-depth state-of-the-art analysis in LiDAR inertial odometry.
Highlighting the problem of drift, the author gives some interesting references on GNSS fusion.
However, I believe that this remark should be completed by systems that have tackled the drift issue with loop closure like SA LOAM or SUMA.
Otherwise, the related work section highlights a strong bibliographical work.

## Major remarks

* The definition of the feature matrix is not clear at all. It is hard to understand how projecting the feature point cloud along the height direction results in a 2D matrix made of vector entries (that is a 3D matrix to me). 
A way clearer explanation is required for what seems to be the core contribution of the paper
* There is a big ambiguity about the GNSS / IMU estimator here. It is not clear if the IMU is the same as the one used for the LIO. Even worse, it is not clear that the GNSS/IMU system used is not the same as the one used in groundtruth.
This point must be clarified as this may compromise the validity of the results.
* The concept of hybrid sliding window is misleading. According to the paper, the only poses optimized in the LIO are the consecutive frames so the sliding window optimization problem only uses keyframes to fix the gauge. 
I personally don't see the point of mentioning them while dealing with the LIO.

## Minor remarks:
* I: "... point cloud map.In summary..." add space after dot
* I: "constructs constraints" sounds weird
* I: "An keyframe" remove n
* III - B 1) : Why for some keyframe indices these are put as exponent? Sometimes $l_{o-M}$ or $l^{o-M}$, unify this notation or justify the difference that is not clear
* III - B 1) : A lots of terms in Equation (2) are not explained. If there is no explanation about this equation, I believe that it is not worth mentionning
* III - B 1) :  "equation(Eq.3)" you can sum this up as Equation 3
* III - B 1) : there is no 2), why setting a subsubsection?
* III - C : "feature matrix (FM)" put in capital letters the first letters of the accronym
* III - C : "feature vector (FV)" same as before
* III - C 1) : Don't remind the accronym FM
* III - C 2) : The definition of the feature is not clear, in particular it is not obvious that $\mathbf{C}_{ij}$ and $\mathbf{L}_{ij}$ have the same size
* III - D 1) : "GNSS/IMU signals are ..." GNSS signals only are blocked, why do you mention the IMU here?
* III - D 1) : "respectively.Based on ..." again, space after the dot
* III - D 1) : "textcolorred[cite wicrf,wicrf2]" big typo
* IV - A 1) "LM significantly reduces both ATE and ARE" what is LM?

## Conclusion

This paper presents a LiDAR / GNSS / IMU fusion pipeline that competes with state-of-the-art on urban scenarios. The novelty here, is a keyframe selection method based on a Feature Matrix.
I particularly appreciated the results on the AvgFrames metric. 
However, despite a rather complete experimental study and promising results, I believe that this publication is not suited for a publication at RA-L. 
The only contribution of this paper is the keyframe selection method that is minor and poorly explained.
I think that for such a high standard journal, an additional minor contribution is necessary such as a public dataset or another novelty in the estimation pipeline.
Moreover, the paper is not very well written overall with many repetitions while important information is missing. 
I believe that after an in-depth proof read and some adjustments, this document would be suited for a conference publication.
