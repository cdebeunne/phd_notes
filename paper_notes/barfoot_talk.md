# Where Can Machine Learning Help Robotic State Estimation?
Tim Barfoot

link: https://youtu.be/z9IeZ_U0uqY
___
Notes:
---
* real world != perfect world of linear gaussian estimation
* Continuous time trajectories: x(t) but discrete measurements -> GP regression, separation principle= solve at measrements times, then interpolate at query times
* Lie Groups: banana distribution is Gaussian (Gaussian in the Lie Algebra), ATTENTION exponential map can only be used for perturbation C = exp(phi) * C_op 
* Gaussian Variational Inference: Unsupervized learning of parameters = m-step of variationnal inference (learning motion and observation model), graph optimisation of a batch of poses = e-step, enable derivative free state estimation, optimizes mean and covariance
* Read : *Unsupervised Learning of Lidar Features for Use in a Probabilistic Trajectory Estimator*
* Koopman/kernel Embeddings: Idea is using higher dimensions to simplify a problem, transform non linear state equation to high-dimensional linear system, learning the high-dimensional bilinear system from data and convert it to a linear system, representer theorem used to go back to the normal state   