# Robust Visual Odometry Using Position-Aware Flow and Geometric Bundle Adjustment

Author: Cao & Co

Year: 2021

Notes:
---
* Geometrical method for optical flow < deep learning based methods
* trained depth and optical flow models online w/ BA geometric framework

Method:
* dense inverse depth + optical flow => BA => sparse inverse depth and SE(3) transform between frames
* optical flow model use a probability volume (4D) that is convoluted in 2D instead of a simple CNN that estimates the flow
* Filtering before BA: forward and backward flow estimation for occlusion mask, 3000 best pixels according to forward backward score and then outlier rejection w/ essential matrix (optical flow gives dense pixel association, now they have sparse)
* T initialization for BA done with PnP algorithm
* Self supervised training with photometric error on reconstructed images from optical flow net or depth net
* In practice both network can't be trained in the same time. First optical flow is trained, then with fixed weight on optical flow, depth net is trained and then refining on both nets

Discussion:
* joint geometry and learning algorithm generalize better than pure learning 
* low dynamic range => hard for learning

Commentaires:
---
Super papier d'apprentissage non supervisé pour l'odométrie, bonne ref, en parler avec zhunjun