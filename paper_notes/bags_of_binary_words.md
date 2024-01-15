# Bags of Binary Words for Fast Place Recognition in Image Sequences

Authors: Galvez Lopez

Year: 2012

Notes:
---
* BRIEF descriptor and FAST keypoints: very robust for our usecase 
* FAB MAP: great image to image loop detector at that time
* BRIEF descriptors: Bi(p) = 1 if I(p+ai) > I(p+bi) 0 sinon. ai and bi chosen randomly in advance and the size of the vector is a parameter
* Here, bi is chosen close to ai and L_b=256 (size of vector) and S_b=48 (patch size)
* Binary descriptor => fast to compare

Image Database:
* W visual words in the descriptor space computed offline
* Clustering process to build a binary tree from the visual words (appart from the leaves, each node is the average of the cluster)
* Each feature of a bag of word go through the tree from top to leaves going through the nodes that minimizes its hamming distance
* for each word in the vocabulary tree, a list of images where it was observed is stored (inverse index)
* for each image the nodes of the trees of each local features are stored (direct index)

Loop detection:
* database query of a bag of word v_t leads to a lists of candidates v_t_i. Some of them are discarded with a normalized similarity score
* Creation of Island: grouping of matches in the same timestamp interval. The Island with the highest similarity score is selected
* Check of the temporal consistency of the Island and then the image with the greatest score is selected
* A geometric check is performed: an essential matrix is computed with RANSAC and the features are associated with the ones that passed through the same node at the level l of the tree

Commentaires:
---
Algorithme technique, mais la structure de données est assez compréhensible. BRIEF n'est pas invariant à la rotation => ne marche que dans le cas planaire. A relire 
