# Nonlinear Graph Sparsification for SLAM

Author: Mazuran

Year: 2014

Notes:
---
* Inference on factor graph is equivalent to NLS optimization
* Formulation of the good optimization pb of marginalization and sparsification:
    * pb convex
    * conserve block structure 
    * general approach
    * local approach (only in markov blanket)
* demonstration of KLD being an instance of MAXDET problem, which makes it a convex problem
* optimzation based on limited memory Projected Quasi Newton (PQN)
