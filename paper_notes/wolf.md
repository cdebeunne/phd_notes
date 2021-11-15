# WOLF: A modular estimation framework for robotics based on factor graphs

Authors: 
Joan Solà, Joan Vallve-Navarro, Joaquim Casals, Jérémie Deray, Médéric Fourmy, Dinesh Atchuthan and Juan Andrade-Cetto

Year: 2021
___
Notes:
---
* Extend factor graph to build more general estimators (self-calibration & dynamic quantities other than pose)
* Tree structures with nodes like *Sensors*, *Processors*, *Captures*...
* factors = relation between state blocks and measurements
* processors = front-end, factors = back-end, problem= tree management
* YAML information provider => no need to compile the code for a new problem
* Pre integration not only for IMU but for every proprioceptive sensor
* 2 types of tracker: frame to frame (scans or depth map) or feature to map (april tag & co)
* Future work: multi-threading processors for real-time applications

___
Commentaires:
---
Condensé de ce qu'il faut savoir sur wolf: top!
