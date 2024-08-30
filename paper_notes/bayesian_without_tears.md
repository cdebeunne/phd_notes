# Bayesian Statistics Without Tears: A Sampling-Resampling Perspective

Author: Smith

Year: 1992

Notes:
---
* goal find the posterior, from data $x$ and a prior distro $p(\theta)$:
$$
p(\theta | x) = p(\theta; x) p(\theta) / \int p(\theta, x)p(\theta) d\theta
$$
* so the goal is to generate samples from a distribution $h(\theta)$ continuous wrt to $g(\theta)$ 
* Proposes methods to generates samples from $h(\theta)$ that is a normalized density $h = f / \int f$ with samples of $g$ and the functionnal form of $f$
* Introduces the rejection method and the weighted bootstrap
* For the Bayes theorem we have $f_x(\theta) = p(\theta; x) p(\theta)$ and the sampled distribution is precisely the posterior $p(\theta | x)$
* Illustrative example with a sum of binomial distribution