# E-NeRF: Neural Radiance Fields from a Moving Event Camera

Author: Cremers

Year: 2023

Notes:
---
* Estimating a NeRF assume illumination and slow motion
* NeRF = volumetric scene representation
* Works with fast motion and high dynamic range with event cameras
* NeRFs represent the scene by a multilayer perceptron (MLP) combined with differentiable rendering
* Combines events and frames 
* NeRF is a MLP that does takes a 3D point and a direction and returns a color and a density $F_{\theta} (\bold x,  \bold d) = (\bold c, \rho)$
* The differentiable volume rendering function $$ is given in *NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis*
* A NeRF is able to learn high frequency details by embedding the input to a larger dimension in the Fourrier space $F_{\theta} = F_{\theta}' o \gamma$
* For each event $e_k$, two rays are taken at different timestamp $r_k, r_{k-1}$ and are used to compute the loss (need more knowledge about event cameras)
* Design a loss for non event pixel also
* The final loss is a weighted combination of both
* *ESIM* is a simulator of event data