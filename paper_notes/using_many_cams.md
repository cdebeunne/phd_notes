# Using Many Cameras as One

Author : Pless

Year : 2003

Notes:
---
* use a network of cameras as a single imaging device
* generalized camera model: a pixel is equivalent to a *raxel* that defines a cone from which the pixel captures the light
* here the raxels are simplified as a line that can be represented with Plucker vectors
* Plücker representation is made of two vectors $q, q'$:
    * $q$ is the direction of the line
    * $q'$ is defined as $q' = q \times P$ for every $P$ that lies on the line
* In the camera frame, the Plücker representation will simply be $(\pi^{-1}(u), [0, 0, 0]^T)$
* A pair of Plücker vector intersects if
$$
q_1 . q'_2 + q'_1 . q_2 = 0
$$
* Fall back on the classic formula for perspective cameras (i.e. with $q'_1 = q'_2 = 0$)
$$
q_2^T R [t]_{\times} q_1 = 0
$$
* Come up with the optical flow equation, that depends on the angular velocity, the translationnal velocity and the depth:
$$
\dot{q}=-(\vec{\omega} \times q)-\frac{(\vec{t} \times q) \times q}{\alpha}
$$
* Use the Fisher information matrix to determine which camera configuration is the best 
* the measurement is assumed to be the optical flow $\vec{u}$, it derives an expression of $h_i(\vec{t}, \vec{\omega}, \alpha, q, q') = \vec{u}$ that leads to an anlytical formula of the Fisher info matrix
* Then a simulation is conducted on a uniform distribution over the parameters $\vec{t}, \vec{\omega}, \alpha_1, ..., \alpha_n$ with $n$ the number of pixels
* The best configuration seems to be two aligned cameras facing opposite directions