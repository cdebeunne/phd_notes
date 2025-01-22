# Non-submodular Visual Attention for Robot Navigation

For more comfort, this text can be compiled as a markdown file.

This paper presents a method to select a relevant subset of landmarks for visual inertial navigation (VIN). This is formulated as a maximisation problem on a MSE based function on a set of landmarks that are likely to be seen on a given time horizon. Inspired by the method proposed in [1], the authors use an IMU model and a vision model to derive the information matrix of the future states. This information matrix will be used to evaluate the objective function that is suposedly non-submodular. Three different approaches are proposed: a simple greedy algorithm whose performance bounds are theoretically demonstrated, a randomized greedy algorithm whose approximation bound are demonstrated and a linearization based greedy algorithm whose derivation are explicited and that seems to be an efficient alternative.
An experimental comparison of these methods and the one proposed in [1] is performed on a trajectory of the EUROC dataset. Moreover, the submodularity ratio and the curvature are evaluated for a small set of selected landmarks on this trajectory.
An additionnal experiment was conducted on a small scale scenario using objects as landmarks. Here, the proposed simple greedy algorithm is evaluated using only 1 or 2 landmarks in the estimator.

### Related works

The related works are summarized in the introduction. This makes sense as this subject was not widely studied in the community and then, a state-of-the-art summary is a great introduction for this paper. Feature selection for visual navigation is fully covered and some related sparsification problems in other fields are cited.
However, the state-of-the-art in Visual Inertial Navigation is not described at all. It is not the core of the paper but at least a quick reminder on the most commonly used techniques for VIN (filtering, smoothing...) and reference to a recent paper on the subject (e.g. [2]) should be mentionned.

### Major remarks
* The EuRoC dataset is only used here to compare the different approaches. It could have been used to demonstrate clearly the interest of the method by comparing it to a baseline one several trajectories. I warmly suggest the authors to exploit more deeply this dataset for more meaningful results and stronger conclusions. 
* The second experiment also raises some questions. How are the object landmarks parameterized? Are these single 3D points bellonging to the object like their barycenter? What cost function do you use in ISAM2? If it is a reprojection error what do you reproject? You should make those points clear. 
Moreover, I find this experiment a bit weird. When you are already dealing with a small number of landmarks such as in this scenario, is there really a gain in run time to select a subset of landmarks? The practical application on a classic VIO with hundreds of landmarks is obvious but there not really. You should demonstrate clearly that the run time of both the back-end and the selection mechanism is better than no selection at all in this particular scenario. Moreover, you state "For the visibility check within the future horizon, we use the future true YOLO detections." I find this a bit disapointing that you use future images in a scenario that is supposed to be realistic. Why don't you use the motion model to extrapolate if a landmark can be seen in future frames? I would expect that if you perform your own experiments you should apply your methodology on a proper application use case: use control inputs for future states, a real IMU and without using any future data inputs.
* Part V, the concluding remarks, is very disapointing. You don't remind any of your experimental results (in a way, it highlights their weaknesses) and you only give one sentence for future research work. And by the way, the proposed perspective sounds very cliche and could be generalized to any robotic paper. What improvement can you bring? What new application can you imagine? Can you generalize this approach to other sensor modalities?
There are plenty of open questions on this subject that could be raised. As a personnal advice, I would say that the conclusion is the last impression you leave to most readers, you should really work on it.
* A lot of inacuracies and inconsistencies appear in the references. I won't go into detail but an important proof read is needed here. You should really pay attention in the consistencies of the references when you submit a paper, this can affect negatively the credibility of your work.

### Minor remarks 

* I - "MSE, our primary performance metric, is not submodular" How do you know that? Do you have a reference or a quick explanation?
* I - You state "We defer some of the proofs to an appendix" but only one of them is in the appendix. For consistency, I think you should also add the proofs of proposition 1 and 2 to facilitate the reading.
* I - You should mention the experiments in the introduction
* II - A) You abreviate respectively here (resp. ...) but not in the rest of the text. You should be consistent.
* II - A) You introduce "$\preceq$, $\prec$, $\succ$, $\succeq$" but these are never used
* II - C) Put capital letters on p and d to highlight the abreviation in "yields a positive definite (PD)"
* III - How do you know that (2) is NP hard? do you have any reference?
* III - A) Lemma 1 : remove the space in the citation under parenthesis ( [21]) or you can also give it a name like *Approximate non-submodular maximization*
* III - A) I also believe that lemma 1 should be a proposition
* III - A) Below Theorem 1 you should precise that the proof is in appendix
* III - A) There is a confusion in Equation 12: $\bar{\alpha}$ and $\bar{\gamma}$ are supposed to be bounds but you define them in (12) with an inequality while in the demonstration you define $\bar{\gamma}$ with an equality. Btw you should also define $\bar{\alpha}$ in the demonstration. Proof read is needed on both theorem I statement and demo.
* III - B) You forgot to add the exponent $\eta$ in the sentence "Thus, the terme $\epsilon / c$ ..."
* III - C) Equation 16 a minus is missing before the Trace
* IV - In the first paragraph you repeat twice "proposed feature selection frameworks", try to reformulate.
* IV - Be consistent when you refer to the EuRoC dataset, sometimes you put italic letters, sometimes not
* IV - A) remove VI in "with a VI (stereo) visual-inertial sensor." That sounds repetitive
* IV - A) What is this $f$ function on Fig 3? It can't be the objective function as you pretend that the lower the better
* IV - A) And how do you compute a single value on an entire trajectory? Do you do the average on each keyframe? This should be mentionned
* IV - A) I don't agree with the statement "the linearization-based greedy algorithm demonstrates comparable performance with superior time complexity when handling larger values of κ". The linearized line is barely below only after $\kappa=110$, Fig3 doesn't allow to draw this conclusion. Additionnal experiments or clearer results are needed.
* IV - A) Again I believe this statement is a bit far fetched "Interestingly, as indicated by Fig 3, the time complexity of the randomized greedy algorithm slightly decreases as κ increases." The behaviour of the randomized curve only seems noisy. 
* IV - A) On Fig 5 I find it strange that alpha is equal to 0 on the bounds of the plot, is it indeed the computed value? It looks like outliers or missing values in the plot, can you check on that?
* IV - A) Specify the unit for the vertical axis on Fig 6
* IV - A) Explain more in details how you compute the performance metric on Fig 6. I don't understand how can you come up with a L1 norm of hundreds of meters.
* IV - A) Precise what value of $\kappa$ you have used to obtain the trajectory on Fig 7
* IV - B) You should do two subfigures for Fig 8
* IV - B) Again, put the unit of the translationnal error on Fig 9
* IV - B) "Due to the stochastic nature..." Explain why it is stochastic, I guess it is due to YOLO but it is not obvious
* IV - B) On the bottom of Fig 9 you pretend that you display the landmark selection for a greedy method with $\kappa = 2$. However, it seems that no more than one landmark is selected per frame.


### Overall

This paper presents rigourously some theoretical concepts to tackle the problem of visual attention for VIN but, to me, it fails to deliver a convincing experimental validation. Despite a few missing points, the introduction is well conducted and the contribution sounds clear.
The theoretical concepts are well explained and, appart from a few typos, the proof are correct and clear.
However, the experiments are not satisfying for such a high quality journal. The EuRoC dataset is barely used with only one trajectory evaluated, a lot of results are not clear or misleading and some conclusions are not obvious at all. 
It is very disapointing in comparison to [1] that presents a very complete evaluation of the method using several simulations and exploiting every sequences of the EuRoC dataset. The authors clearly failed to demonstrate the pertinence of their work, despite an interesting attempt with an homemade dataset but that is poorly exploited.
As a consequence, I believe this paper is not suitable for publication at T-RO. However, I believe that with major revisions (in particular on the experimental part), the authors could make this work suitable for an eventual journal publication. I hope that my comments will help the authors to produce better scientific productions in the future.

### References
[1] L. Carlone and S. Karaman, “Attention and anticipation in fast visual-
inertial navigation,” IEEE Transactions on Robotics, vol. 35, no. 1, pp.
1–20, 2018.4

[2] Campos, C., Elvira, R., Rodríguez, J. J. G., M. Montiel, J. M.
and D. Tardós, J. ORB-SLAM3: An Accurate Open-Source Library for Vi-
sual, Visual–Inertial, and Multimap SLAM. IEEE Transactions on Robotics,
vol. 37, no. 6, pages 1874–1890, 2021.