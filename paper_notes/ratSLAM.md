# RatSLAM

* inspired from rat (or rodent) brain hippocampus
* leads to large scale navigation
* brain cells used for navigation spotted in rat brains: 
    * place cells (cells that are activated only when the rate is at a given place)
    * head direction cells (fires when the head is oriented in a specific direction)
* the brain maintains a *code* that describes a 3dof pose that is maintains through visual and proprioceptive inputs


Heading Attractor (head direction cells)
* Continuous Attractor Network to model brain cells: with spreading connections and inhibition connections
* Self Motion cues add connections in the network
* Local views cells that are associated to a specific orientation and fires to it when activated

2D attractor (place cells)
* boundary problem solved with wrapping connectivity

First Exp (2003)
* 2m * 2m square with artificial landmark
* the error keeps low in the short term and diverge in the long run: because of ambiguity of pose cells for some observation that must lead to multi hypothesis tracking 

Version 2
* now use a combination of place cells and orientation cells as pose cells
* But in 2005, new conclusions in biology: a single place cell can be activated on several places as well as conjuctive cells => pose cells organised in a grid 
* experiments in a building: lots of relocalization that leads to discontinuities => the network cannot be interpreted as locations anymore

Version 3 
* add an experience map = semi metric map
* desambiguate distinct scenes that looks similar
* experience map = graph : graph relaxation for loop closure, pruning to limit memory, path planning

Suburb experiments
* a raw VO gives the motion info
* 42 loop closure detected 
* not metrically correct, but the topology is well represented

Conclusion
* start with biology, then engeneer where it fails 