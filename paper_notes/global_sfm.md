# Global Structure-from-Motion Revisited

Author : Pan

Year : 2024

Notes:
---

* On the contrary to COLMAP that is incremental, GLOMAP is a global approach
* global = recover the camera geometry for all input images at once considering all two-view geometry in the graph
* same as colmap for corespondence search (BoW for overlapping pair and brute force feature matching with RootSIFT)

### Related works
* Perform global pose estimation for each frame thanks to rotation averaging then translation averaging 
* rotation averaging = ensure the relation $R_i^T R_{ij} R_j = I_3$ with robust optimization
* translation averaging is the same: estimating a global pose consistent with all pair wise translation (necessitate a *parallel rigid* graph)
* incorporate 3D strucuture to improve accuracy of camera pose estimation
* Sfm with global triangulation and global BA

### Contributions

* performs joint global triangulation and camera position estimation
* the error function is a constraints on unrotated camera rays : the error is bounded 