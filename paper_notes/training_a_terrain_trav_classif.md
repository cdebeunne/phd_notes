# Training a terrain traversability classifier for a planetary rover through simulation

Author: Robert A Hewitt

Year: 2017

Notes:
---
* LiDAR scans are divided into a grid containing number of points, variance, mean height, rover orientation, mean height of adjacent cells, absolute height difference
* train a simple MLP to classify each cell as traversable or untraversable using simulated data
* cell grid are the size of wheel
* the simulations are randomly generated: a rock is untraversable, while ground is traversable
* The NN is trained using a Extended Kalman Filter
* 3D scans produced by a 2D lidar with a tilt device