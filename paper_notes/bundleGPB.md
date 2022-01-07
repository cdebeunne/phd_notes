# Bundle Adjustment on a Graph Processor

Author: Joseph Ortiz & Andrew Davison

Year: 2020

Notes:
---
* IPU = new calcul unit for AI with massive parallelisation 
* GPB = general case of loopy belief prop.
* Not competitive on CPU but take 
* BP = algorithm for computing marginal from joint probability
* When distributions are Gaussians, LGBP converges to the correct marginal
 
BA factor graph:

* 2 factors: measurement factor and prior factor
* prior factor = comparison to a prior distribution
* prior errors are required to set scale
* linearization of the projection function
* parametrization with information matrix and vector for measurement model

GPB:

* variable nodes update their belief by taking a product of incoming messages from adjacent factors
* synchronous scheduling: all factor nodes relinearise and send messages at each iterations 
* message damping to stabilise the convergence

Results:

* Metrics to compare BA is ARE (average reprojection error) 

Commentaires:
---
Pas appris grd chose de nouveau, revoir la notion de marginalisation.
Idée appliquer GPB à la fusion de capteurs
