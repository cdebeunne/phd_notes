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

This paper presents a multi sensor fusion framework for anomaly detection and path planning in unstructured scenes, especially containing vegetation. Data from a LiDAR, an RGB camera and the odometry of a legged robot is encoded using deep neural networks to generate low dimensionnal feature vectors. The predicted trajectory from a path planner is turned into a binary image that is also encoded as a feature vector. These vectors are turned into a graph that is ponderated with reliability scores from image and laser sensors. Scan reliability is based on the number of points belonging to edges and planes while image reliability is based on the brightness and the number of salient points. This graph, whose theoretical consistency is demonstrated in the paper, is then fed into a Graph Neural Network (GNN) to infer the success probability of each steps of the trajectory planned. This method, called GrASPE, is used in a local path planner in an iterative scheme to generate an anomaly free trajectory. Evaluation on 4 different scenarios is performed to cover a wide range of challenging data (e.g. cluttered scenes, low lighting conditions...). A comparison with path planners, other anomaly detection algorithms and ablated version of GrASPE concludes the efficiency of the proposed algorithm. Moreover, experiments in real time were conducted on a robot mounted computer, the inference rate being high enough despite the heavy GNN backbone. The author concludes on the limitations of its model and propose to consider the holonomic behaviour of a quadruped robot and the fusion with force sensor for future researches.

## Related Work

In the introduction, the author refers to sensor fusion for robotic applications and also highlights the need to consider GNN in outdoor scenarios. The related work part details the work done about sensor fusion, anomaly detection and finally about methods to estimate the probability of future failures. This related work part is complete and is the proof of a strong state of the art study. However, I suggest to add a reference about end-to-end learning of control policies which have been studied with sensor fusion in unstructured environments (e.g. Nguyen et al, *Autonomous Navigation in Complex Environments with Deep Multimodal Fusion Network*)

## Specific Comments

* I, par 1 : in the first sentence, you should stick citations to applications "such as delivery[1], agriculture[2], surveillance..." OK
* I, par 3 : you should highlight "Deep Learning" with capital letters as you are using the abbreviation DL OK
* I, par 4 : Same remark as before with Attention based CNN (A-CNN)
* I, par 4 : Why is there a - after poorly? poorly lit is in two words OK
* II, C: capital letters for Supervised Variationnal AutoEncoders (SVAE) OK
* III - A : The list of symbols table crops some notations and it is not necessarily easy to read. Maybe a short paragraph would be more compact and more lisible. OK
* III - B : in the formulation it is stated $\hat{E}_t \in [0, 1]^T$ which is a bad notation. $\hat{E}_t$ it is a vector $\in \mathbb{R}^T$, you should write it as in III-C $\hat{E}_t = [p_t, ... p_{t+T-1}]$ with $p_t \in [0, 1] \forall t$. OK
* IV - B, 4) : Missing braces around the kernel sizes {3,2,2} OK
* IV - C, 2) : Be consistent with the notations, here you wrote lidar without capital letters instead of LiDAR   OK
* IV - D, par 2: You use i.e. twice in the same sentence to explain edge weights. This is clumsy, you should reformulate. OK
* IV - E: You can use A-GNN to save space, the notation was introduced before. OK
* IV - F, proof lemma1: It is not explicit from (7) that $r_{i,j} = r_{j,i}$, you should specify it or cover more cases in the definition. OK
* IV - F, proof lemma2: $m_{i,j}$ is not what is in the exponent from (6), it is $\lambda \cdot\left|f_{v e c}(i)-f_{v e c}(j)\right| \cdot\left(2-r_{i, j}\right)$. Proof read is needed there. OK
* V - E: Again, don't hesitate to use FNR and FPR abreviations to save space
* Biblio: CVPR acronym is given in [5] but not in [29] and [31] (and the pages are given in [29])


## Global Comments
* Too much remarks into parenthesis or using e.g., i.e.. It degrades the fluidity of the article
* Proof read needed in the text and in the biblio part

## Multimedia

The video is very relevant and illustrates well some parts of the paper. The recording of failure case is particularly interesting to highlights the limitations of the methods.

## Conclusion

To conclude, this paper presents an original method based on deep learning to fuse multi-modal information for pro-active failure detection and demonstrate impressive experimental results on a challenging dataset. The document is very dense in information and this leads sometimes to a lack of clarity and readability. Even if the content is very satisfying, the paper needs a proper reformating to fit the standards of a journal paper. 

## NEW REMARKS

The author has answered most of the comments and a proof read has been obviously conducted. The new version is clearer, to me it suits the standards of a journal paper. 

I have just a comment about the modification done in the experimental part. It is good to add a non threshold dependant metric, as requested by one of the reviewers. But why not keeping at least one of the two previous threshold dependant metric? For instance, I believe that in this context the false positive rate was a very relevant metric: a false positive could lead to actual failure in practice. 

Finally, I have two minor comments to add:

* III-A : This paragrah is way clearer than the previous table. However there is a small typo: "from a lidar" => "from a LiDAR".
* III-B : Ê_t is well defined now, but the notations are differents than in IV-A. In fact, you don't even need to remind the format of the vector to the reader in IV-A.