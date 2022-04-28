# Hybrid Scene Compression for Visual Localization

Author: Sattler

Year: 2019

Notes:
---

* memory limit for localization in a 3D model
* small set of point is represented with full apearance info but large set of points with compressed info (hybrid)
* CNN method like poseNet
* small set of pt used for high quality correspondences for full descriptor matching 
* RANSAC variation to handle both feature types and 3D covisibility
* Averaging SIFT descriptor on all images from which the point was triangulated
* Vocabulary based feature matching, word = one index (integer)
* Scene compression (i.e. reducing the number of points) using covisibility and vocabulary (penalizes words that are over represented)
that selects $\mathcal{P'}$ the subset of descriptor unique points
* big set of point will only be described by word (quantized desc), they will result in multimatch disambiguated by pose

Modified RANSAC:
* Samples with a high probability co visible points in quality match
* P3P for calibrated cameras and P4P when focal is not known
* check inliers with both quality and quantized matches