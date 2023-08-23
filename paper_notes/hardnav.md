# HARDNAV - Simulator for Benchmarking Robust Navigation and Place Recognition in Large, Confusing and Highly Dynamic Environments

### Introduction

* Interesting angle of attack to the problem with bio inspired SLAMs

### Related Works

* "These mostly focus on task
such as ”vision-language navigation” in which deep learning
models are trained to perform tasks specified in human
language." : You repeat task twice and "specified in human language" sounds weird, I suggest "specified with human words".
* It could be interesting to talk about real world challenging benchmark e.g. OIVIO dataset and 4 seasons dataset (they differentiate from KITTI and EUROC in which the scenarios are pretty basics)
* When you describe the subT challenge, you specify details into parenthesis twice in a single sentence. Try to reformulate it into two more concise sentences

### Hardnav simulator

* for sensors like IMU, LiDAR or GPS you should introduce the notation the first time you mention them
* other interesting sensor suite: bimono/stereo cameras, wide FOV cameras (a dedicated plugin already exists in Gazebo)

### Robust navigation and place recognition benchmarks

* "Essentially, the task is that the robot
should actively explore an environment after being
kidnapped, and in some given amount of time give an
answer as to in which previously seen area (for example a
bounding box in the world, as described in Sec. III-B) it is." Remove the as after answer
* "(e.g. in the Forest1 environment... )" Man this is the longest text into parenthesis I have ever seen ahah. Simply do another clear sentence starting with "For instance"
* "We believe this problem to be a vital subproblem for the
following task:" Which task? It is strange not to end a sentence like this (or to end it in a subsection name). You should rephrase

### Future work and discussion

* The third bullet point is a bit confusing, try to stick to only one quesion + explanation per bullet point

## Global remarks

* Sometimes you make too long sentences, with a lot of details in parenthesis and so on. This makes your point less clear and can confuse the reader. Try to split your ideas into more concise sentences
* I know this can be a lot of work for you, but maybe you should record a few sequences that makes ORB SLAM or other soa  SLAM algorithm fail. Adding a "First results" section would really step up the quality of the paper, even if you can not experiment the full potential of the simulator
* Otherwise this is some really original work with an original point neuro science oriented point of view. You should keep working in this direction :) Good job man!