# Accurate and Efficient Stereo Processing by Semi-Global Matching and Mutual Information

Author: Hirschmüller

Year: 2005

Notes:
---
* Corelation based methods (for stereo matching) are time efficient but is incorrect for discontinuity
* Idea: pixelwise matching of mutual Information with 2D smoothness constraint
* Occlusion detection
* Mutual information = Hi1 + Hi2 - Hi1i2
* Rien compris au MI matching cost :o
* Energy cost E(D) that supports smoothness, but is a 2D function
* Turn this into a 1D function in all direction (????)
* Complexity is O(WHD)

Commentaires:
---
papier hyper compliqué, étudier l'entropie d'une image et voir le matching basé corelation (idée, tester plusieurs méthodes de stereo matching et comparer pour stereo vision)