# KN-SLAM: Keypoints and Neural Implicit Encoding SLAM

Author: Wu

Year: 2024

Notes:
---
* SLAM with implicit representation show poor localization and no loop closure with RGBD
* Fused feature based localization with loop closure and implicit representation (the one of NICESLAM) 
* IMAP uses a single mlp to represent the entire scene
* Nice slam uses multiple encoder-decoder pair at different resolution for scene representation
* vote KF with overlap ratio 
* perform joint optimization on reprojection, depth and color loss to refine pose and scene representation parameters
* loop closure with simple kp matching and pose graph optimization + refine scene representation parameters