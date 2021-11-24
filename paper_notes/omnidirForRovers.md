# Omnidirectional stereoscopic vision systems for planetary exploration rovers

Author: Alex Torres & co

Year: 2012, iSAIRAS conference

Notes:
---
* Complex camera models that requires reevaluation of vision algorithm
* Fisheye lenses do not respect single viewpoint constraint (??)
* single viewpoint constraint (SVC) if each ray going through the *effective pinhole* would have crossed a single *effective viewpoint* 
* Calibration with Scaramuzza method implemented on matlab vs Using a beam collimator
* Beam Collimator with gimbal generates a correction map for each pixel of the raw image according to a theoretical model, enables compensation for stereovision bench as well that leads to epipolar rectified images
* Omni Directional Vision Sensor HL-X52 for hypercatadioptric sensors
* Fish eye lens: Fujinon
FE185CO57 that follows an *equidistant* projection
* Collimator calibration worked poorly with catadioptric but well with fisheye lens
* Figures of projection of the pixels on the ground thks to calibration parameters to compare both sensors
* Fisheye lenses were finally chosen however: lack of single effective viewpoint
* solid angle subtented by the pixel (??)
* Coaxial mount chosen -> column search for epipolar search (izi)
* Expansion factor (??)

Commentaires:
---
Explication complète de l'aboutissement vers un montage coaxial stéréo fisheye, quelques points d'ombres à éclaircir avec alex