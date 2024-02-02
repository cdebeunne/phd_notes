# Kimera2: Robust and Accurate Metric-Semantic SLAM in the Real World

Author: Abate

Year: 2024

Notes:
---
* Enhance Kimera:
    * Better feature tracking
    * More efficient KF selection
    * New pose graph optimization backend
    * New inputs (rgbd, mono, wheel odometry)
* New trend: LLM for hierarchical spatial representation
* Use BetweenFactor of GTSAM to improve odometry with external inputs (LiDAR / wheel etc..)
* Feature binning with an input mask
* KF voting based on disparity between frames (wtf? c nul)
* Previously, rejects bad loop closure with Pairwise Consistent Measurement Set Maximisation, now with graduated non convexity
* ablation studies blablabla