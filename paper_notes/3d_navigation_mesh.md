# 3D Navigation Mesh Generation for Path Planning in Uneven Terrain

Author: Pütz

Year: 2016

Notes:
---

* 3D triangular mesh with pc
* used for traversability and roughness on uneven ground

### Related work:

* octree maps can be used in a ros package for planning (= occupancy map)
* triangle mesh are more flexible: *Rough terrain reconstruction for
rover motion planning*

### System:

* take as input an arbitrary mesh (here mesh generated with *Organized fast mesh*)
* Navigation mesh generation (height, roughness and co) that check for lethal contexts with safety thresholds 
* Graph edge region smoothing around lethal regions 

### Mesh generation

* outlier removal
* organized point cloud: point stored in a $\theta$ and $\phi$ 2D matrix structure = depth image (enables fast and robust normal estimation)
* mesh generation as in *Rough terrain reconstruction for
rover motion planning* with a rule to filter shadow edges


### Navigation mesh 

* two graphs: a triangle graph and a vertex graph
* for each edges a cost function taking into account: distance between vertices, local roughness, height difference or riskiness
* local roughness computed as an average fluctuation of normals in a neighbourhood
* height difference is defined as the maximum difference in the $z$ direction in a vincinity around a vertex $v$
$$
b(v) = \underset{u \in \mathcal{N}(v)}{max} \left | \frac{(p(u) - p(v)).z}{|z|} \right |
$$
* then standard graph search algorithm can be applied for path planning 
* heavy roughness and heigth, bound of the mesh are marked as lethal
* inflation algorithm around lethal region to smooth the mesh

### Navigation

* A* search on the graph for path planning
* velocity command can be deduced by height and roughness

### Experiments and conclusion

* 3D scans in a stop and go fashion with 2D Lidar
* low cost computation, smooth planned path 
* classification based on local height is not enought   