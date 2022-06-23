# Illumination Change Robustness in Direct Visual SLAM

Author: Park

Year: 2017

Notes:
---
* photometric cost is based on brightness consistancy assumption
* evaluation of lighting change robust pose estimation method

Direct Image alignement:
* look at the robustness of photometric residual in isolation
* Uses RGB-D images to ignore the depth estimation pb
* Pb: an image $I$, with a depth map $D$ needs to be aligned with a template $T$. We need to find the transformation $\mathbf{M}$ that warps every pixels $x$ with depth $d$ on $T$:
$$
W(x, d, \mathbf{M}) = \pi_T \ (\mathbf{M} . \pi^{-1}_I (x, d))
$$
Thus the image alignement pb can be formulated as:
$$
C(\mathbf{M}) = \frac{1}{\Omega} \sum_{x \in \Omega} \rho(T(W(x,d,\mathbf{M})) - I(x)))
$$
* Dense descriptor images can be used as well $D_T$ and $D_I$ the pb is then
$
\begin{equation}
C(\mathbf{M}) = \frac{1}{\Omega} \sum_{x \in \Omega} \rho(D_T(W(x,d,\mathbf{M})) - D_I(x)))
\end{equation}
$
* But do we compute the descriptors on the original image or on the warped image? 

Robust Formulation:

* Global median bias normalization (GMedian): (1) is normalized by the median of the residuals
* Global affine model: intensities of one image are transformed by an affine function $I(x) = (1+\alpha)I(x) + \beta$, each iteration jointly optimize $\Delta \mathbf{M}, \delta \alpha, \delta \beta$
* Zero Mean Normalized Cross Corelation: maximises ZNCC for image alignement
* Mutual information: compute MI on the occurence probability of intensities
* Gradient Magnitude: align gradient magnitude instead of image intensities (descriptor based method)
* Local mean bias normalization: locally normalizes pixel intensities by substracting from them the mean intensity of a patch around them (descriptor based method)
* Descriptor Field: compute a descriptor image using convolutions
* Census Transform: binary descriptor based on intensity comparison (classic) (descriptor based method)

Evaluation:
* the testing is performed frame to frame
* metric: drift in cm/second
* methods convergence probabilities facing rotation, translation and illuminatino change on synthetic data: Brightness Consistency Assumption (BCA) fails for small illumination changes
* BCA is the fastest in runtime performance, all implementations are run on GPU
* Direct method better to refine pose, Indirect (SIFT) better for large changes