# GrASPE: Graph based Multimodal Fusion for Robot Navigation in Outdoor Environments

Author: Weratoon

Year: 2023

Notes:
---

* multi sensor (RGB, LiDAR, legeed odom) traversability and planning in unstructured env
* encoder network to represent sensory inputs as feature vectors then GNN (graph neural network) to predict trajectory success probability
* Experimental evaluation on SPOT   
* Sensor noise and failures in unstruct env: motion blur and low lighting for cams, vegetation for lidar
* CNN are limited as they cannot capture complex correlations between modalities, GNN leverage this
* Build a feature graph to train an attention based GNN (AGNN)
* Also perform reliability estimation of sensor inputs based on the number of salient features of scans and images to weight the graph