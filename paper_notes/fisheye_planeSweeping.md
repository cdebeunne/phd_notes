# Real-Time Direct Dense Matching on Fisheye Images Using Plane-Sweeping Stereo

Authors: Christian Häne, Lionel Heng, Gim Hee Lee, Alexey Sizov, Marc Pollefeys

Year: 2014

Notes:
---
* Adaptation of plane sweeping algorithm (*space-sweep approach to true multi-image
matching*) to fisheye camera model
* plane sweeping allows direct matching on multiple images ie dense stereo matching (shit...)
* two camera models: unified projection (*Single view point omnidirectional
camera calibration from planar grids*) and FOV (*Straight lines have to be straight*)

Plane sweeping algo:

* Two images I_l (reference), I_r
* set of plane hypothesis PI
* for each plane PI_m, all the pixels of I_r are mapped on the plane in the reference view (with an homography): this is I_r,l,m
* The dissimilarity between I_l and I_r,l,m is computed 
* For each pixels, the plane with the lowest matching cost is chosen and its depth is computed 

Commentaires:
---
J'ai l'impression que ça marche que pour des environnements structurés... En plus, ça utilise le GPU. C'est mort pour nous donc...

Cependant, ça peut être un bon exo à implémenter
