# Long-Term Simultaneous Localization and Mapping with Generic Linear Constraint Node Removal

Author: Bianco

Year: 2013

Notes:
---
* experiments on 34h hours of operations, 147km on 27 aquisition sessions
* steps:
    * marginalization over elimination clique
    * CLT approximation 
    * factor recovery
    * factor replacement
* CLT $p(x_i, x_j)$ is computed with Schur Complement *marginalization is easy in the covariance form, since it corresponds to extracting the appropriate subblock from the covariance matrix, while in the information form, it is hard, because
it involves calculating the Schur complement over the variables
we wish to keep*
* ensure Jacobians are invertible by root shifting  
* GLC = computing observation model from factors obtained by CLT approximation using eigen value decomposition, reparametrized as relative transform

Graph management scheme:
* policy: remove spatially redundant nodes i.e. one node every 3m, when going in visited places, keeping the more recent nodes
* batch multi session: batch node removal between aquisition sessions removing redundant nodes by keeping the newest one OR by keeping nodes with highest score i.e. number of successfull matching
* online removing: adding a new node and if spatially redundant, GLC remove it OR doing the opposite i.e. keeping the most recent node and removing its neigbours

Experiments:
* experiments with LiDAR 3D and ICP
* graph management with ISAM2 + GPS 4 gt
* performance on translation error is worst with online strategy: data association is harder when env is changing with time
* 10 ms to remove a node with GLC
* similar error than full graph but 4.4 faster to solve
* KL is not low, but lowering it remains for future work
* remove chain of nodes leads to bad graph shape => random node elimination