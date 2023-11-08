# Real-time CNN-based Spacecraft Pose Estimation on COTs Reconfigurable MPSoCs

Author: Posso

### Intro

* pose estimation of a known spacecraft
* real time inference on a commercial hardware ready for space for a pose estimation CNN
* contrib: optimization of the CNN + FPGA dataflow
* Clear-space 1 (2026) will need pose estimation alg
* challenge hosted by ESA on the Spacecraft Pose Estimation Dataset (SPEED)
* proposes implementation on a CPU and on an FPGA
* study the energy efficiency (?)
* 12 orientation bins per dimension (?)

### Related Work

* Keypoint methods + soft classification = soa, but requires quantization for being embedded
* Quantization = approximating a NN that uses floats by a NN with low bits numbers
* Usually int8 quantization, may lead to 1.32W for inference
* Overall incomplete works on NN embedding for SPE

### CPU implementation

* Mobile-URSONet is a classic pose estimation CNN
* First train the Float32 model (Mobile-URSONet), then Quantize it to int8, the Quantized model is trained
* Then fuse Conv, BN and Relu layers and export the CNN (?)
* Compile the CNN with TVM (?)
* Auto schedulling with TVM (?)
* details the impact of every step of the workflow on the perfs, position is more affected than orientation
* measures power consumption, FPS and FPS per watts

### FPGA implementation

* First train the float32 model, then perform Quantization Aware Training on several (146) configuration to find a good tradeoff
* Engeenering stuff with an FPGA simulator to get a compatible node that minimizes parallelization (and then FPGA resources)
* develop a new CNN architecture for FPGA implementation
* what is a FIFO (?)
* what is a stride (?)
* all the layers are quantized to 8 bits, then decrease bit width of some layers and check the influence
* figure 3b: shows how the number of MAC (multiply accumulate operations) is envenly distributed among CNN layers
* figure 4: no significant perf drop over 3 bit quantization
* quantization affects more orientation than position estimation
* Only the backbone is quantized due to FINN (https://finn-hlslib.readthedocs.io/en/latest/) limitations, the head remains Float32
* Fig 5: study the influence of a binarized layer while the other are in 8 bits
* The first layers seems very sensitive to quantization: set to 4 bits for most them and 6 for the first depthwise convolution (https://medium.com/@zurister/depth-wise-convolution-and-depth-wise-separable-convolution-37346565d4ec) and 3 bits for the last 49 layers = *Mixed precision quantization*
* FPGA and Brevitas implementation has the same perf

### Comparison

* better energy efficiency than soa 
* potential future work by moving head of nn to FPGA too
* same methodology to keypoint based SPE NN
* exploring other backbone (see which one can be the best quantized)


# Notes

* explain what TVM is 
* Even if it was detailed in a previous paper, a remainder of the methodology used for pose estimation is necessary. It is hard for the reader to understand all the details about CPU and FPGA implementation without a big picture of the structure of the network

This paper introduces two methods to implement a Spacecraft Pose Estimation algorithm on a space ready, low-power chip. The algorithm aims at estimating both position and orientation of a known spacecraft using a Convolutionnal Neural Network (CNN). The state of the art has more focused on accuracy improvements instead of finding a good treadoff between performance and energy efficiency. This is what this paper is aiming at. The first method proposes a CPU implementation of this CNN using Int8 quantization of the network, fusion of several layers and TVM compilation. The second method is about an FPGA implementation of the backbone of the CNN. It is modified to be compatible and optimized for the MPSoC and then a meticulous study of mixed-precision quantization is performed to reach a good treadoff. Finally, even if the literature doesn't provide a lot of similar works, these implementations outperform existing systems in term of energy efficiency. 

The related work part goes a bit fast on the state of the art techniques for SPE. The author should explain further what are keypoint detections and soft classification methods instead of simply rephrasing the introduction. Similarly, a quick explaination on what is quantization of neural network should be also written in the introdution or in related works. On the other hand, a strong analysis of similar works on SPE embedded on low power computer is provided, which is a good point.

Global comments:
* Even if it was detailed in a previous paper, a remainder of the methodology used for pose estimation is necessary. It is hard for the reader to understand all the details about CPU and FPGA implementation without a big picture of the structure of the network.
* Is it possible to compute the metrics of the energy efficiency of the Float32 model or the Int8 model for FPGA? It could be interesting to have an idea of the efficiency of quantization in terms of energy efficiency for SPE on this platform.
* Sometimes too much acronyms are used without explanations, especially about the tools used for hardware acceleration (TVM, FINN, FIFO, FINN-ONIX, DDR). I know it can be hard to avoid them, but it makes the reading uncomfortable. You should introduce them and use them sparsly. 
* Very interesting interpretation of the quantization effects. To me, this is the real contribution of the paper. However, it is more an engeenering than a scientific contribution.

Minor comments:
* I: "spacecraft pose estimation (SPE)" once this notation is introduced, you can use it in the entire paper. Sometimes you reuse the entire formulation, save some space and gain consistency by using SPE everywhere. 
* II : "Only Javed et. al. propose a module-wise quantization algorithm, an intermediate between layer-wise quantization and uniform quantization applied to spacecraft pose estimation." Should be rephrased: an interemediate what? (method, techniques...) And add a  coma should be added before applied
* II : "trade-off" unconsistent notation, in the rest of the text "tradeoff" is used (both are valid in my opinion but you should stick to one)
* III-A learning rate $1e^{-3}$ and $1e^{-4}$
* III It lacks information here: which dataset is used for training? which dataset is used for evaluation? what is the ESA score? The SPEED dataset was introduced previously but is it the one used in your experiments
* IV-A: "but it only took us a week on a real-world dataset that (CONTAINS?) few images using a..." a word is missing
* IV-B: "figure 3a ... Figure 3c" Consistency on notations, stick to a f capital letter or not for the entire text.
* IV-B: "in Section IV-C" Consistency on notations, in the rest of the text you don't use capital letter for the s
* IV-C: "In addition, our experiments, show that activations are..." remove the coma after "experiments"
* IV-D: "This accurate functional equivalence across both software and hardware implementations is the result of a meticulous design and validation of the neural network architecture and the FPGA workflow." I have a doubt on this interpretation, to me it is more about the quality of the FINN tools to provide a reliable framework for hardware acceleration of NN. 

Overall, this paper details a strong ingeneering work and follows a rigourous procedure to implement a light SPE neural network on space ready hardware. However, I believe that the scientific contribution  to the robotic community is not strong enough to justify a presentation at ICRA. Moreover, it lacks consistency on notations and requires proofreading. At this stage, this quality paper is more suited for a conference dedicated to space robotics like i-SAIRAS. 