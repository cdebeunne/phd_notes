# OVPC Mesh: 3D Free-space Representation for Local Ground Vehicle Navigation

Author: Ruetz

Year: 2019

Notes:
---
* sf *On Visible Point Cloud Mesh*, applied to rough terrain navigation, fullfil RT constraints
* Uses the *General hidden point removal operator* that reduces a PC to visible points from a certain viewpoint
* *Octomap* : uses an octree structure (slow map queries for insertion or lookup)
* *Voxblox* : voxel hashing strategy which allocates fixed size blocks in regions of the map that contain data
* On the contrary, this method does not rely on grid discretization
* *On fast surface reconstruction methods for large and noisy point clouds* reaches near RT
* Super slides on convex hull algorithms: https://tildesites.bowdoin.edu/~ltoma/teaching/cs3250-CompGeom/spring17/Lectures/cg-hull3d.pdf

##  Method:

* performs a radial transformation of every LiDAR point and forms a convex hull on it
* Use the gravity aligned world frame to compute the surface angle $\alpha$
* A polygon is traversable if $\alpha < \alpha_{max}$ and $\in [-\pi/2, \pi/2]$, anfd if the maximum height difference between the vertices is smaller than a thresh
* Generates a point cloud from the mesh with all the vertices as a map representation for path planning 

## Experiments

* Use a robot centric point cloud buffer of 20-30 scans
* Use RRTConnect path planner
* Simulates noisy pc => normal estimation is better using OCPV mesh
* Three runs on rough terrain of several hectometers
* Has a smaller and less spreaded run time than octomap and elevation mapping
* able to handle hoverhang scenarios (roof)
* Very sensitive to outliers in LiDAR data => voxel filter needed 
* Convex hull algorithm ensures a watertight mesh

@INPROCEEDINGS{ovpcmeshRuetz,
  author={Ruetz, Fabio and Hernández, Emili and Pfeiffer, Mark and Oleynikova, Helen and Cox, Mark and Lowe, Thomas and Borges, Paulo},
  booktitle={2019 International Conference on Robotics and Automation (ICRA)}, 
  title={OVPC Mesh: 3D Free-space Representation for Local Ground Vehicle Navigation}, 
  year={2019},
  volume={},
  number={},
  pages={8648-8654},
  doi={10.1109/ICRA.2019.8793503}
}
