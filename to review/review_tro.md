# Non-submodular Visual Attention for Robot Navigation

This paper presents a method to select a relevant subset of landmark for visual inertial navigation (VIN). This is formulated as a maximisation problem on a MSE based function on a set of landmarks that are likely to be seen on a given time horizon. Inspired by the method proposed in [1], the authors use an IMU model and a vision model to derive the information matrix of the future states. This information matrix will be used to evaluate the objective function that is suposedly non-submodular. Three different approaches are proposed: a simple greedy algorithm whose performance bounds are theoretically demonstrated, a randomized greedy algorithm whose approximation bound are demonstrated and a linearization based greedy algorithm whose derivation are explicited and that seems to be an efficient alternative. An experimental comparison of these methods and the one proposed in [1] is performed on a trajectory of the EUROC dataset. blabla calculated. An additionnal experiment was conducted on a small scale scenarios using objects as landmarks. The VIN exhibits a clear performance improvement using the simple greedy algorithm is observed using only 2 landmarks in the estimator.

### Related works

The related works are summarized in the introduction. This makes sense as this subject was not widely studied in the community and then, a state-of-the-art summary is a great introduction for this paper. Feature selection for visual navigation is fully covered and some related sparsification problems in other fields are cited. However, the state-of-the-art in Visual Inertial Navigation is not described at all. It is not the core of the paper but at least a quick reminder on the most commonly used techniques for VIN (filtering, smoothing...) and reference to a recent paper on the subject (e.g. [2]) should be mentionned.

### Minor remarks
* How did you come up with $f$? 
* This is not clear how landmarks from Yolo detections are used. Do you use the barycenter of the object? Do you use several keypoints on the object? You should clarify this
* The conclusive section is pretty deceiving. In particular I find that the proposed futur research could be applied to any paper in robotics that doesn't specifically tackles multi-robot system. Why don't you propose some improvements to your method or some radically different approaches? 

### Overall

In comparison to [1], the quality of this paper is clearly below in terms of content and clarity of presentation.

### References
[1] L. Carlone and S. Karaman, “Attention and anticipation in fast visual-
inertial navigation,” IEEE Transactions on Robotics, vol. 35, no. 1, pp.
1–20, 2018.4

[2] Campos, C., Elvira, R., Rodríguez, J. J. G., M. Montiel, J. M.
and D. Tardós, J. ORB-SLAM3: An Accurate Open-Source Library for Vi-
sual, Visual–Inertial, and Multimap SLAM. IEEE Transactions on Robotics,
vol. 37, no. 6, pages 1874–1890, 2021.