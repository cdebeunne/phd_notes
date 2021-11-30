# Measurement of Three-Dimensional Environment with a Fish-Eye Camera Based on Structure from Motion - Error Analysis

Authors: Kenji Terabayashi & Co

Year: 2009

Notes:
---
* Use a polynomial fish eye camera model rf = k1 theta + k3 theta^3 + k4 theta^5
* Feature points tracked with KLT or SIFT
* ray vector p = [sin t cos p, sin t sin p, cos t]
* E (essential matrix) computed with 8 points algorithms and RANSAC
* Translation and rotation obtained with essential matrix
* skew lines = lines that neither intersect neither are parallel
* Triangulation with mid point method
* Inaccurate point removal with partial derivative
* Bundle adjsutement in a RANSAC fashion for less computation

Commentaires:
---
Super papier de structure from motion, big up!

