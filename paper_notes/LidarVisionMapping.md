# Map Construction Based on Lidar Vision Inertial Multi-sensor Fusion

Authors: Chuanwei Zhang, Lei Lei, Xiaowen Ma, Rui Zhou, Zhenghe Shi and Zhongyu Guo

To review

Notes:
---
* Lidar Vision IMU SLAM in a factor graph framework with loop closure
* Visual front end with orb features 
* When a loop closure is detected ICP is performed with lidar to add a new constraint in the factor

Commentaires:
---
Introduction:
* l2. slam -> SLAM (unifier la notation)
* l14 too many and
* 3rd contribution Lidar instead of radar
* LiDAR instead of lidar
* First contribution is not a contribution to me
* Figure 1: an arrow is missing 

mal écrit, pas hyper clair, pas mal de coquilles et de répétitions

Previous Work:
* l2 dependency
* l4 featureS
* p2 l15 LOAM instead of loam
* p2 l22 VLOAM instead of VLAOM
* p2 l17 LiDAR instead of radar
* p2 l19 odometry not odometer

Quel torchon...

Methods:
* A - l13 maximum a posteriori
* A - l14 prior
* A - eq3 is difficult to read
* B, a - visual front end not clear at all: re explain the downsampling process
* B - 1) The points*
* B - what is the difference between P_i and 'P_i ???
* B Figure 2 is too small and subimage c looks like a random point cloud: change the view or the color code
* C - l6 processing process is clumsy
* C - l19 prior (again...)
* C - eq 10 looks wrong you don't add the values for error computation
* D - l5 LiDAR!!!
* D - why do you mix p and F to refer to points?
* D - eq 14 is not clear, what is f?
* E - why is there a dot on the x_k?
* F - l7 scan matching 
* G - dot on eq15 ?

Experiments:
* A - l2 at school*
* A - figure 8 use relative timestamp

The langage is often clumsy and there are many typos. The mathematical notations are not rigorous enough and formulas are also subject to typos (which doesn't help for comprehension). 
