# Terrain trafficability analysis and soil mechanical property identification for planetary rovers: A survey

Author: S. Chhaniyara

Year: 2012

Notes:
---

* All relevant terrain characterisation methods used on planetary missions and those under considerations are covered
* Different challenges Moon vs Mars: communication, sandy vs rocky...
* Limitations of wheeled robots on steep slopes and loose terrain => legged robots
* hazards: surfaces that may pose a threat to rover mobility e.g. soft soil that leads to spirit permanent immobilization

### Terrain Characterisation methods

* provides primary information about the environment the rover needs to negotiate
* use of satellite imagery, remote sensing
* soil void ratio can be computed from thermal data (IR multispectral)
* use of ground penetrating radar to classify ground type, low mass (45g) and low power (1W)
* MER rovers carry image based terrain characterising algorithms: identify rocky and sandy areas, slopes and dangerous areas: but computationnally expensive algorithms and ambiguities 
* LiDAR are more robust, but require more power, data compression and do not provide information on the soil substrate
* Mars surface missions have not instrument to measure physical properties of the soil, only estimates in situ (dans son milieu) shear strength (resistance au cisaillement) and density with rover mechanical interaction => use of penetrometer in other missions
* quantitative description of wheel performance: soil vertical deformation (weight and slip) and soil shear deformation (due to tractive thrust) => enhance control algorithm
* Finite Element Modelling (FEM) for wheel soil interaction
* Terrain classification with microscopic imaging or drive torques under the rover to infer grain size
* optical flow based slip estimation technique
* instrumented wheels to asses soil-wheel interaction
* bevameter: terramechanic device to measure mechanical properties of the ground
* cone penetrometer to asses the ability of a given vehicle to be supported by the terrain

### Trade off 