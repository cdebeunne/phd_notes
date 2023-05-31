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

## Related work
* Limitation of filtering methods to fuse distincts features (images and point cloud)
* Deep learning used for sensor fusion but assumption of feature availability
* Anomaly detection models can be trained with trivially labeled data (traversable or not)
* Proactive anomaly detection?
* REMARK: 3D LiDAR can be problematic in vegetation also

## Background and Formulation

* Table 1 is badly formated 
* Returns a probability vector of success of a trajectory $E_t \in [0,1]$
* REMARK $E_t$ is not in [0, 1], it has an higher dimension
* Use of a graph NN to represent complex correlations between measurements

## GrASP

* Inputs: $I_t, P_t$, the concatenation of the T past velocities {v_t-T ... v_t} and the predicted trajectory from time t as a binary image (the predicted trajectory is projected on a blank image)
* Outputs: the sucess probability vector $E_t = \{ p_t...p_{t+T} \}$
* each sensor input is preprocessed using encoder networks, resulting in feature vector representations $f_{vec} = [f_{img}, f_{pc}, f_{vel}, f_{traj}]$
* Use a resnet backbone for img, point net for pc, convolutionnal networks for Velocity, pooling and convolutionnal nets for trajectory image
* Measure the reliability of an image using a score that combines brightness and the number of FAST corners detected
* REMARK: no consistency in LiDAR notation
* Measure the reliability of a scan using the number of planar and edges (based on the classic roughness score)
* A graph linking all the elements in $f_{vec}$ is generated and whose adjacent matrix is computed using the reliabiity score
* The graph is passed through a network based on GCN to return the output prediction
* demo to demonstrate that the graph is undirected with non negative weight: a bit clumsy
* Why is it necessary to state lemmas for the graph features?
* Adapts a Dynamic Window Approach (DWA) planner using reliability information, it returns an optimal set $(v^*, \omega^*)$ for the next $T$ timesteps
* The planner ignore obstacle avoidance when the scan is not enough structured 
* When a trajectory is generated, the current data is fed into grasp. When some $(v^*, \omega^*)$ of the trajectory are affected to a probability less than a thresh, it is added to the set of non admissible velocities and the planner is ran again.

## Experiments
* REMARK: "We use the following evaluation metrics..." Which metrics? You explain the metric two paragraphs after this sentence, you should reformulate
* Do the distinction between pliable and non pliable plants
* Ablation studies without A-GNN, how is it possible? => turn the graph + GNN into a simple 1D convolution network
* Success rate: what does it mean? Is it evaluated by hand?
* Different scenarios for unstrucutered scenes: plants, bushed, hanging leaves, trees, tall grass...
* Acheives rt on a embedded computer
* Assumes non holomic robot dynamics => generates to holomic robots (that has 6 Dof)


# REVIEW

## Sum Up 

This paper presents a multi sensor fusion framework for anomaly detection and path planning in unstructured scenes, especially containing vegetation. Data from a LiDAR, an RGB camera and the odometry of a robot is encoded using deep neural network to generate low dimensionnal feature vectors. The predicted trajectory from a path planner is turned into a binary image that is also encoded as a feature vector. These vectors are turned into a graph that is ponderated with reliability scores from image and laser sensors. Scan reliability is based on the number of points belonging to edges and planes while image reliability is based on the brightness and the number of salient points. This graph, whose theoretical consistency is demonstrated in the paper, is then fed into a Graph Neural Network to infer the success probability of each steps of the trajectory planned. This method, called GrASPE, is used in a local path planner in a iterative scheme to generate an anomaly free trajectory. Evaluation on 4 different scenarios is performed to cover a wide range of challenging data (e.g. cluttered scenes, low lighting conditions...). A comparison to path planners and other anomaly detection algorithms concludes the efficiency of the proposed algorithm that results in a decent sucess rate on all the scenarios. Moreover, experiments in real time were conducted as the inference rate is high enough (despite it is the lowest of the proposed method). The author concludes on the limitations of its model and propose to consider the holonomic behaviour of a quadruped robot and the fusion with force sensor for future researches.