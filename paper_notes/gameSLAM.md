# GTP-SLAM: Game-Theoretic Priors for Simultaneous Localization and Mapping in Multi-Agent Scenarios

Author:

Year: 2022

Notes:
---
* SLAM as a game with an optimal solution
* usefull in high dynamic scenarios (traffic)
* this uses an iterative best response (IBR)
scheme, in which each player takes a turn solving for their
optimal strategy while assuming all other players’ strategies
are fixed
* IBR can be solved with a factor graph framework

Preliminaries:
* there are $N$ players: one *ego player* and the others
* jointly estimate trajectories off *ego player* and *non-ego playerS*
* the *ego player* observes $N_l$ landmarks and players observe other players positions
* Nash Equilibrium : a set of control input reaches a Nash Equilibrium if no player can lower their cost by deviating their input, the other players input being fixed