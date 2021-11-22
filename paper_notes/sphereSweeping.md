# Real-Time Sphere Sweeping Stereo from Multiview Fisheye Images

Authors: 
Andreas Meuleman Hyeonjoong Jang Daniel S. Jeon Min H. Kim

Year: 2021

Notes:
---
* 4 fisheye cameras to cover 360° FOV
* Binocular stereo model: *Binocular Spherical Stereo*
* Use spherical coordinates for pixels
* For a pixel in c0 there is a sphere volume in which the pixel can be matched (fig2) depending on the distance
* A good matched is found when the pixel value of the warped pixels in c1 = I_c0
* Selection of the best camera for stereo matching (osef)
* Double sphere model for camera calibration (*the double sphere
camera model*)
* Edge preserving downsampling and upsampling designed for parallel computing
* For depth estimation on blind pixels (occlusion) diffusion kernel based on inpainting direction
* All results performed with GPU
* Quantitative evaluation with a synthetic dataset with blender

Commentaires:
---
Papier intéressant avec pas mal d'astuces sur le filtrage et le traitement des images fish eye. Cependant certaines parties sont dures à comprendre, et ces méthodes sont destinées à la parallélisation 