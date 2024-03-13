# NeRF: Representing Scenes as Neural Radiance Fields for View Synthesis

Author: Mildenhall

Year: 2020

Notes:
---
* First paper on nerf: method to synthetize novel views of complex scenes
* Scene is represented by a MLP whose input is 5D $(x,y,z,\theta, \phi)$ and output is density and color $(R, G, B, \sigma)$
* Needs camera with known pose