# An Efficient Global Optimality Certificate for Landmark-Based SLAM

Author: Holmes & Barfoot

Year : 2023

Notes:
---
* Global optimaliy certificate established for pose SLAM but not for lmk based SLAM
* The data matrix required to compute the certificate 
* *SE-
sync: A certifiably correct algorithm for synchronization over the special
Euclidean group* proved that global optimal solutions can be found for PGO (pose graph optimization)
* They consider 3D landmark SLAM with simple 3D measurements in the pose's frame without outlier measurements
* Divide the SLAM into three subproblems : rotation averaging, multiple point cloud registration and pgo:
$$
\begin{gathered}
J_r=\sum_{(i, k) \in \overrightarrow{\mathcal{E}}_p} w_{i k}^r\left\|\boldsymbol{R}_{o i} \widetilde{\boldsymbol{R}}_{i k}-\boldsymbol{R}_{o k}\right\|_F^2, \\
J_b=\sum_{(i, j) \in \overrightarrow{\mathcal{E}}_b} w_{i j}^b\left\|\boldsymbol{R}_{o i} \tilde{\boldsymbol{y}}_i^{j i}-\left(\boldsymbol{m}_o^{j o}-\boldsymbol{t}_o^{i o}\right)\right\|_2^2, \\
J_t=\sum_{(i, k) \in \overrightarrow{\mathcal{E}}_p} w_{i k}^t\left\|\boldsymbol{R}_{o i} \tilde{\boldsymbol{t}}_i^{k i}-\left(\boldsymbol{t}_o^{k o}-\boldsymbol{t}_o^{i o}\right)\right\|_2^2.
\end{gathered}
$$
* $||A||_F^2 = tr(A A^*)$
* They combine those 3 subproblems into a genereic QCQP (Quadratically Constrained Quadratic Program) : both the objective function and the constraint are quadratic functions 
* Build a problem that is a function of $M$ (all the translations and  landmarks) that is unconstrained and $R$ (all the rotations) that is in $SO(3)$ to apply the *variable projection method*: the optimal $M^*$ is computed and injected to get a problem on $R$ only
* The final problem is like:
$$
\begin{aligned}
\min & p(\boldsymbol{R})=\operatorname{tr}\left(\boldsymbol{Q} \boldsymbol{R}^T \boldsymbol{R}\right) \\
\text { w.r.t. } & \boldsymbol{R}=\left[\begin{array}{ll}
\boldsymbol{R}_{o 1} \quad \cdots & \boldsymbol{R}_{o N_p}
\end{array}\right] \\
\text { s.t. } & \boldsymbol{R}_{o i} \boldsymbol{R}_{o i}^T=\boldsymbol{I}, \quad\left(\forall i=1, \ldots, N_p\right)
\end{aligned}
$$
* Finally find a sufficient optimality condition is found on the Lagrange multiplier
* Classic method : difference between primal and dual optimal values 
* Propose an efficent way of computing the *data matrix* $Q$ with linear complexity (as an iteration of a sparse local solver for BA)
* Eigen values can be computed with worst case $O(n^3)$
* Shows that their method is better than a naive approached on SE_synced that considers landmarks as degenerate poses