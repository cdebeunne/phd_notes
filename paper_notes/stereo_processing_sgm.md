# Stereo Processing by Semiglobal Matching and Mutual Information

Author: Hirschmüller

Year: 2008

Notes:
---

* complexity linear to number of pixels and disparity range
* MI used to handle radiometric differences
* pb with occlusion: you can do left / right association
* SOA is based on global energy cost
* derive a pixel wise MI based cost function, and a sum over all pixels gives a global cost function
* This cost function needs a prior on disparity images, that is obtained recursively on ds images
* add penalty terms for local changes of disparity in the vincinity of the pixel (smoothness) that is ponderated by the intensity gradients
* such a 2D global minimization is NP complete
* aggregate the cost of all the 1D pixels costs that ends up in the pixels (to smooth again)
* subpixel refinement by interpolating a cuadratic curves on the 3 lowest costs and finding the min
* Compute the two disparity images switching base and match image and remove outliers 
* performs multibaseline stereo with : a weighted mean of all pixels + remove outliers that are within 1 pixel from the median
* post processing: remove peaks, fit planes on untextured areas, interpolates occluded areas with the disparity of the occludee, interpolates missing values with a median disparity

TOCHECK stereo:
* est-ce que l'aller-retour est activé?
* combien de directions pour l'agregation de couts
* utiliser la valeurs médiane pour la fusion de costmaps