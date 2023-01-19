# NICE-SLAM: Neural Implicit Scalable Encoding for SLAM

Author: Zhu

Year: 2022

Notes:
---

* Neural implicit representation produced over smoothed methods and are not scalable
* Uses hierarchical scene representation and pre trained geometric priors for indoor reconstruction
* Uses RGBD input
* IMAP = first SLAM with neural implicit representation uses a single MLP to represent an entire scene -> cannot handle large scenes
* The core of nice SLAM is hierarchical grid based neural encoding -> allows local updates
* Stores latent code of local geometry and optimizes directly on them