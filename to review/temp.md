## Related Works

The related work section details firstly the deep learning methods applied to image transformation. Then generative networks are introduced on several applications like 3D reconstruction (NeRF) or image-to-image translation with GANs. Most similar works are:
* Bridge-GAN: three GANs models are trained with a supervised approach to generate three alternative views
* Boosted IPM: Incrementally performs small transformation in the bottleneck of an auto encoder network to generate a bird's-eye view incrementally

Only Boosted IPM is compared to the method as it requires a similar training approach. Overall, this analysis of related works is very complete and detailed. 

## Review

* Fig 1: Maybe there should be zoomed images on artifacts and their corrections instead of inviting the reader to zoom
* I, par1: Acting as robotic investigators on our behalf, these spacecraftS are equipped... 
* III, eq1: it is not clear on which incrementally transformed image this loss is applying, why not using a similar notation as in eq 7?
* IV, A: How did you handle the failures of Boosted IPM in the quantitative evaluation? Were they removed? 
* IV, B, par2: The scores are supposed to be a mean. But a mean on what? On all your training data? Did you split your dataset into training and validation data? Even if it is unsupervised learning, you can be more explicit on your evaluation dataset
