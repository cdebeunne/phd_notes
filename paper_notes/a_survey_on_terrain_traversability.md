# A Survey on Terrain Traversability Analysis for Autonomous Ground Vehicles: Methods, Sensors, and Challenges

Author: Paulo V. K. Borges

Year: 2022

Notes:
---

## Intro:
* focuss on off road scenarios
* Chhaniyara et al., 2012 for planetary terrain analysis
* study camera, lidar or fusion of two solutions

## Taxonomy:
* obstacle detection -> occupancy maps (negative obstacle = holes)
* terrain classification: (grass, asphalt...) semantic
* traversability analysis: generate a "difficulty/cost map", depend on the type of robot
* model based method: based on explicit model e.g. sand is yellow pixels, robot cannot drive 20 degrees slopes
* data driven = learning methods (SVM = traditionnal learning vs. deep learning)
* proprioception may be used in terrain analysis: slippery terrain with wheel odometers, rugged terrain with vibrations observation (IMU)
* trav mettrics : terrain shape with roughness (small scale variation of the height of a surface) and slope using statistical analysis of 3D pc
* also metrics plateform dependant like kinematics and probabilistic metrics taking uncertainties into account
* difficult to define precise performance evaluation (except for classification) for unobservable metrics (difficulty), may be checking the configuration of the robot 

## Vision based methods:
* 3 classes : non learning methods, traditionnal learning methods and deep learning methods

non learning methods:
* stereovision method developped for MER mission
* terrain classification with color calibration and maximum likelihood estimator -> not robust to illumination changes and weather conditions
* disparity map computation -> elevation histogram
* (Bajracharya et al., 2013) stereo visual odometry + near field terrain map with classification and negative obstacle with voxel maps 
* negative obstacle detection is a challenge in night time with passive sensors 
* but their computationnal cost is predictable

traditionnal learning methods:
* extract feature point with descriptors (SURF or SIFT) and train a classifier (BOW, SVM ...)
* (Bajracharya et al., 2008) histogramm based naive bayes classifier with stereo range data
* near to far online learning method: near field stereo info (flat or not etc...) to deduce far-field terrain 
* In terrain classification DL > traditionnal learning methods (Shen and Kelly, 2017)

deep learning methods:
* FCN (fully convollutionnal network) = CNN but with only convolutionnal layer to get coarse output maps
* Encoder - Decoder segNet architecture
* TU net = fuse thermal and rgb images 
* DeepLab = state of the art semantic segmentation used on Curiosity images and for Mars 2020 Landing
* Multimodal dl solutions appear more robust but not suited for RT
* Semi supervised learning = small amount of labeled data available e.g. Mean teacher in  (Wellhausen et al., 2019)
* (Mirza and Osindero, 2014) semi sup with a GAN and fisheye images (GONet) but has experimental limitations 
* Using image flow to improve segmentation: wrap previous features with optical flow, or reduce inference time with Long Short Term Memory
BUT require pixel level labelling on training videos = larger datasets

## LiDAR based methods
* provides accurate and consistent measurements

traditionnal learning:
* SVM to classify trees from 2D scans
* Bayesian generalized kernel inference used for traversability map from LiDAR data (Shan et al., 2018) promising for RT applications
* Using voxels for pre processing to remove outliers
* SVM used to detect negative obstacle 

deep learning:
* SegCloud for segmentation on voxels
* PointNet directly on point cloud

## Alternative Exteroceptive
* IR, hyperspectral and radars usefull for mud and vegetation detection
* Near Infrared used to classify vegetation of the soil with Normalized Difference Vegetation Index
* Shortwave IR can be used to detect water saturated surfaces
* Thermal imagery can also be used to classify surfaces
* hyperspectral imagey used with supervised method for vegetation segmentation
* to overcome lack of labelled images, pb can be formulated as an anomaly detection -> unsupervised methods
* high dimensionnal images (up to 200 spectral band) -> dimensionnality reduction
* UWB radar: low frequency and large bandwidth -> can improve obstacle detection
* mm-wave scanning radar: higher EM frequency than UWB, better resolution and lower noise

## Proprioceptive sensing 
* disambiguate between same looking surfaces (e.g. wet sand vs dry sand), require less processing power 
* vibration: not many work done on body dynamics, spectral analysis of inertial data used to train a classifier for ground type at different speed, recently deep learning based method emerged
* Multisensor with gyros, accelero, wheel encoders, motor current 
* Proprioceptive sensor may be used to estimate terramechanical properties (Martin, 2018) and GP regression is used to extrapolate traversability map
* Audio analysis with CNN -> learning temporal dynamic can improve classification compared to only spatial domain, need to be noise aware training 
* Proprioceptive data from legged robot (Szadkowski et al., 2018)
* joint visual and proprioceptive for robust terrain analysis (Reina
et al., 2018)
* self supervised ML algorithm for training exteroceptive data classifiers using proprioceptive data

## Sensor fusion approaches
* "process and fuse" or "fuse and process" strategies
* reduce uncertainty on stereo dense map using 2D LiDAR, obstacle detection with 3D LiDAR, monocular cam fusion
* Early, middle or late fusion of feature representations (in DNN for instance)
* fusion in learning networks: addition, concatenation or mixture of experts
* not many example of fusion of active sensors like LiDAR - RADAR combination

## Major challenges
* Mud and water detection -> terrain deformation, not necessarily traversable or not...

### Water 
* Water bodies change appearance with reflexion -> most methods combine multiple water cues to find all water bodies
* (Santana et al., 2012) uses chaotic behaviour of optical flow on water surface 
* Use of polarized light to detect highly reflective area from a certain wavelength
* Use of stereo range data to detect reflexion with items below the ground level

### Mud
* Wet soil (darker) or watter puddle
* Segement darker soil with imaging sensors
* Use of polarization contrast
* multimodal approaches needed under shadow or wet conditions

### Negative obstacle
* cliffs, ditches, depressions...
* occlusion and viewing angles results in fewer pixels-on-target -> reduces the detection range 
* can only be seen as a discontinuity -> most methods are using purely geometrical methods 

### Dust
* LiDAR and cameras often fail
* thermal IR, sonar and radar are better for penetrating smoke

### Extreme illumination
* advances in visible spectrum camera good under low light conditions -> day light methods are adaptables
* illumination changes due to artificial illumination

### Other
* deformable terrain
* soiled camera -> augment training datasets with soiled images

## Other
* nice list of annotated datasets
* Terrain8 (Wu et al., 2019)
* CARLA mainly dedicated to urban simulation

## Conclusions
* methods assume 6DoF localization available at all time
* most studies presented off line
* Most traditionnal learning-based methods have shown good success in clearly bounded domain -> deep learning methods are necessary for generalization
* Classification with LiDARs is limited with geometrically similar surfaces
* Fusion of camera and LiDAR seems essential