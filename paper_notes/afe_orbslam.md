# AFE-ORB-SLAM: Robust Monocular VSLAM Based on Adaptive FAST Threshold and Image Enhancement for Complex Lighting Environments

Author: Yu

Year: 2022

Notes:
---
* Adaptive FAST threshold to improve extraction
* Image enhancement based on Adaptive Gamma Correction and unsharp masking 

Image Enhancement:
---
* represent the contrast of an image with the standard deviation of the image intensity
* bright and dark images receive a different treatment. Dark image if the avg of pixel value is below 128, bright else
* Apply gamma corection with tau = 0.3 (for the truncated CDF) for dark images
* Apply the same on negative images for bright images
* Then image sharpening is applied to highlight the contour