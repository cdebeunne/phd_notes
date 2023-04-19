# Unsupervised Surface-to-Orbit View Generation of Planetary Terrain

Author: Chase

Year: 2023

### Sum up

This paper proposes an unsupervised learning method to generate realitic orbit views from surface views taken from an UGV, for machine learning model training. Geometrical method like Inverse Perspective Mapping (IPM) produce unatural stretching and blurring of images. The proposed method leverages Generative Adversarial Networks (GAN) to generate a set of incrementally oriented images from surface to orbit view with improved visual fidelity. The generator is a standard downsample-bottleneck-upsample model that takes as input a surface image and a set of perspective transformation that are performed in the bottleneck of the network. Three different discriminators with the same architectures are trained for different scales of images. The objective function evaluate features similarity w.r.t. IPM images. It is based on a combination of a GAN loss, a feature matching loss and a perceptual loss based on VGG19. The objective function (IF) is a weighted sum on each incremental transformations that gives a more important weight on the first increments (where IPM is supposed to be more accurate). Two additionnal loss are tested that add features comparison with surface images (SF+IF) and with previous IPM images in the transformation chain (IF+IF-1). Qualitative and quantitative evaluation are proposed on the AI4Mars dataset. This results in improvements w.r.t. to IPM and Boosted IPM (also based on a generative model) on image quality and feature similarity metrics. The proposed models are used to train a semantic segmentation model applied to hazardous terrain detection. The dice score on landing data from the Perseverance rover is also improved using the data produced by the proposed generative methods.

### Related Works

The related work section details firstly the deep learning methods applied to image transformation. Then generative networks are introduced on several applications like 3D reconstruction (NeRF) or image-to-image translation with GANs. Most similar works are:
* Bridge-GAN: three GANs models are trained with a supervised approach to generate three alternative views
* Boosted IPM: Incrementally performs small transformation in the bottleneck of an auto encoder network to generate a bird's-eye view of the input image

Only Boosted IPM is compared to the method as it requires a similar training approach. Overall, this analysis of related works is complete and detailed. 

### Minor Comments

* Fig 1: Maybe there should be zoomed images on artifacts and their corrections instead of inviting the reader to zoom
* I, par1: Acting as robotic investigators on our behalf, these spacecraftS are equipped... 
* III, A, par3: You can be more explicit on what is a multi-scale discriminator, it is not straight forward that it means multiple discriminators for different **image resolutions**
* III, eq1: it is not clear on which incrementally transformed image this loss is applying, why not using a similar notation as in eq 7?
* IV, A: How did you handle the failures of Boosted IPM in the quantitative evaluation? Were they removed? 
* IV, B, par2: The scores are supposed to be a mean. But a mean on what? On all your training data? Did you split your dataset into training and validation data? Even if it is unsupervised learning, you can be more explicit on your evaluation dataset
* IV, C: This is an interesting application of your work, it could be interesting to illustrate this segmentation task with an output on the landing dataset. I know that the number of pages can be limiting, it could have been on the video for instance. 

### Conclusion

The proposed method is clearly described and analysed in the applied robotic context of hazardous terrain detection for planetary exploration. The scientific contribution is not outstanding, but the paper is technically clear and the experimental approach is rigorous. Slight improvements can be done on notation clarity and by explaining a few more implementation details. 

### Video

Pas ouf, j'attendais des images de segmentation