# LeNet - 5 Implementation using Brainsmith

<img width="1862" height="438" alt="image" src="https://github.com/user-attachments/assets/1800c4d4-a4c3-4fa1-ae81-fca528112703" />
LeNet-5, from the paper Gradient-Based Learning Applied to Document Recognition, is a very efficient convolutional neural network for handwritten character recognition.

## Structure of the Network

LeNet5 is a small network, it contains the basic modules of deep learning: convolutional layer, pooling layer, and full link layer. It is the basis of other deep learning models. Here we analyze LeNet5 in depth. At the same time, through example analysis, deepen the understanding of the convolutional layer and pooling layer.

<img width="563" height="287" alt="image" src="https://github.com/user-attachments/assets/6812d5b6-9bb9-4732-b2c2-3eb7ec3a2d6a" />

In our case, the model final layers make use of the '_ReLu_' activation function instead of '_tanh_'. Also, we have utilised stride function within the preceding convolutional layers instead of the quantized MaxPool function in Brevitas.
