# About Brainsmith

Brainsmith is a compiler developed jointly by AMD and Microsoft, which serves the purpose of transformation of ONNX models of the neural networks to optimized dataflow accelerators for FPGAs through automated design space exploration. In this repository we have tried to generate RTL design and the final stitched of the LeNet-5 Model.
https://github.com/microsoft/brainsmith.git

Key Stages in the generation of final output:
- Model transformation: Converting ONNX operations to hardware kernels
- Design space exploration: Determining parallelization factors (PE/SIMD)
- Code generation: HLS (C/C++) and/or RTL (i.e. hardware code generation)
- IP Packaging: Create Vivado IP Cores
- Simulation: Verifying correctness with RTL simulation in Vivado (of RTL file/bitfile)

## LeNet - 5 Implementation using Brainsmith

<img width="1862" height="438" alt="image" src="https://github.com/user-attachments/assets/1800c4d4-a4c3-4fa1-ae81-fca528112703" />
LeNet-5, from the paper Gradient-Based Learning Applied to Document Recognition, is a very efficient convolutional neural network for handwritten character recognition.

## Structure of the Network

LeNet5 is a small network, it contains the basic modules of deep learning: convolutional layer, pooling layer, and full link layer. It is the basis of other deep learning models.

<img width="563" height="287" alt="image" src="https://github.com/user-attachments/assets/6812d5b6-9bb9-4732-b2c2-3eb7ec3a2d6a" />

In our case, the model final layers make use of the '_ReLu_' activation function instead of '_tanh_'. Also, we have utilised stride function within the preceding convolutional layers instead of the quantized MaxPool function in Brevitas.

## Installation requirements for Brainsmith Compiler

1. Ubuntu 22.04+ (primary development/testing platform)
2. Vivado Design Suite 2024.2
3. Cmake for V80 shell integration (optional, depends on the applications target HW resource)
4. Python 3.11.*

Ensure 'smith' command line is set-up, which is used to run the compiler and create our streamlined dataflow-accelerators (DFA).

## Brainsmith build flow

PyTorch → ONNX → Hardware Kernels → HLS/RTL → IP Cores → Bitfile (output depends on final step defined in the blueprint file (.yaml)).

<img width="1850" height="823" alt="Screenshot from 2026-06-23 12-06-00" src="https://github.com/user-attachments/assets/f65f8418-b745-4d01-98dd-42e1b1a71dee" />

Our Brainsmith project has been created with the command:

    brainsmith project init lenet

and the configurations are as shown, which is obtained using the command: 

    brainsmith project info --finn
to display along with the finn compiler configurations. 
