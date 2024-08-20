# GS3LAM: Gaussian Semantic Splatting SLAM

Author : ???

Year : 2024

Notes:
---

* Semantic NeRF already exist with additionnal MLP channels to encode and decode semantic information
* Gaussian splatting more efficient than NeRF (dense Gaussian clouds)
* Semantic categories are modeled as implicit features
* processes RGBD data
* each Gaussian is characterized by its position, rotation matrix R, scaling matrix S, opacity o, color c and semantic feature f
* R and S can be combined to compute the covariance of the gaussian $\Sigma = R S S^{\top} R^{\top}$
* compute the color with front to back $\alpha$ blending 
* compute the 2D semantic feature with front to back $\alpha $ blending and optimize a decoder
* Decouple poses and SG field optimization
* compute a mask of unobserved regions to add adaptively newly observation to the field without memory overload
* add a depth regularization term to prevent excessively large or small gaussians (a term that grows for small plus a term that grows for big)
* Instead of covisibility keyframe selection that exhibit a bias depending on the context, use a random kf selection scheme
* for optimization GT data comes from RGB, depth and semantic (which method is used ?)