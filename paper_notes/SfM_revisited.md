# Structure-from-Motion Revisited

Author: Schonerger

Year: 2016

Notes:
---
* General open source framework for SfM COLMAP
* SfM for unordered image set
* Incrementally reconstruct the scene starting from a two view reconstruction
* Build a graph of overlapping images with kp and descr
* Perform geometric verification with $E$ (for calibrated cams) or $F$ (for uncalibrated cams) to obtain a verified scene graph with verified image pairs
* A good image pair selection is necessary for good reconstruction: better if it is a scene densely populated in images
* New images are added by solving PnP (with or without intrinsics in pb)
* Triangulate points for each new image too
* BA is needed to prevent drift to an unrecuperable state
* Performs local BA at each update on the set of most connected images, performs global BA only after growing largely the model
* contributions: 
    * better geometric check: do both homography and epipolar and compare the number of outliers
    * better best view selection: Use a pyramidal grid approach to compare overlapping between image
    * better multi view triangulation: formulate multi view triangulation with RANSAC 
    * Iterative BA with retriangulation and outlier filtering
* BA: sparse direct solver for few hundreds of cams, and preconditionned conjugate gradient for more, remove cams and observations leading to big errors, re triangulate (RT) after BA, perform iteratively {BA, RT, filtering} until no outliers are filtered
* Deal with redundant view: group highly overlapping images and parametrize it as a single camera
* UNCLEAR: how it deals with internal camera parameters 