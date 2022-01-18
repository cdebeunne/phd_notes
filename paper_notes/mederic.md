# Thèse de Mederic Fourmy

Etat de l'art:
---
* Invariant Kalman Filter = KF with lie algebra 
* Ground reaction force => approximation of checking Coulomb cone
* Bayes filter for contact estimation requires a lot of parameter tuning 
* parameter tuning can be reduced by data driven models
* underactuated dynamics = Newton Euler equations = the variation of the system momentum is equal to the external wrench applied to the robot
* wrench = torsion (wrench measurements used to estimate CoM dynamics)
* simplify models for dynamics: LIPM (linear inverse pendulum model)

complementary filter (CF):
* used when there is several sensors used for the same variable but at different frequencies
* we apply high pass filter or low pass filter regarding the sensor then fuse the output

Environment awareness:
* 2.5D maps = 2D maps with height information

Factor graph:
* BA is a special case of factor graph optimization
* BA scales linearly with the number of features whereas filtering scales cubicly
* BA relinearize at each solver step ie linearization gets better whereas filters linearize only once