# A visual introduction to Gaussian Belief Propagation

Author: Davison & co

Year: 2021

Link: https://gaussianbp.github.io/

Notes:
---
* Inference = forming the posterior
* BP (Belief Propagation) => exact marginal computation in tree-structured graph BUT lack of convergence guarantees
* GPB = BP where all factors are Gaussians
* MAP inference => finding Xmap = argmax_X P(X|D)
* marginal inference => finding p(x_i|D)
* Hammersley-Clifford theorem => p(X) = PI f_i(X_i)
* Lack of factor between 2 variables => conditionnally independent
* Factor graphs ~ Energy based models
* BP in 3 steps: Factor to variable messages / Variable to factor messages / belief updates
* BP minimizes the KL divergence
* 2 parametrization of gaussian distribution: Moment form (classical) and canonical form (w/ information vector and precision matrix)
* Precision matrix is sparse and represents the connections in the f graph
* **MAP inference** solves for mu while **marginal inference** solves for both mu and precision matrix
* Covariance scalling =  turning non Gaussian distr to Gaussian
* 