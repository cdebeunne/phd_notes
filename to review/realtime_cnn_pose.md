# Real-time CNN-based Spacecraft Pose Estimation on COTs Reconfigurable MPSoCs

Author: Posso

### Intro

* real time inference on a commercial hardware ready for space for a pose estimation CNN
* contrib: optimization of the CNN + FPGA dataflow
* Clear-space 1 (2026) will need pose estimation alg
* challenge hosted by ESA on the Spacecraft Pose Estimation Dataset (SPEED)
* study the energy efficiency (?)

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


# Note

* explain what TVM is 