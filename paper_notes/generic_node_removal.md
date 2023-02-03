# Generic Node Removal for Factor-Graph SLAM

Author: Carlevaris Bianco

Year: 2014

Notes:
---

* GLC produces a new set of linear factors on the elimination clique that can represent either the true marginalization or a sparse approximation with a CLT
* Application to node removal in long term SLAM
* Demonstrates that pair wise composition doesn't represent fully the dense prior because the resulting measurements are corelated
* Uses root shift to linarize in the local relative frame but this step is optionnal