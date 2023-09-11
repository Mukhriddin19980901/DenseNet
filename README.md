# DenseNet (Densely Connected Convolutional Network) Architecture

<img src="https://github.com/Mukhriddin19980901/DenseNet/blob/main/dense.png" width="1000" height="500" />


  ***DenseNet*** is a deep neural network architecture designed for ***image classification*** tasks . It is characterized by its dense connectivity pattern, where each layer is connected to every other layer in a feed-forward fashion.The architecture was proposed by Gao Huang, Zhuang Liu, Laurens van der Maaten, and Kilian Q. Weinberger. The paper titled "Densely Connected Convolutional Networks" by Gao Huang, Zhuang Liu, Laurens van der Maaten, and Kilian Q. Weinberger was published in January 2017.

  DenseNet introduced a novel connectivity pattern in convolutional neural networks (CNNs), where each layer was densely connected to every other layer in a feed-forward fashion. This dense connectivity facilitated feature reuse and improved the flow of gradients during training, resulting in highly efficient and accurate models.

   The DenseNet architecture has since become widely adopted in computer vision tasks and has had a significant impact on the field of deep learning.***DenseNet-121***  is the original DenseNet architecture with 121 layers. It is commonly used for image classification tasks and is known for its efficient use of parameters.Here are some comparisons with ***ResNet***. 
   
<img src="https://github.com/Mukhriddin19980901/DenseNet/blob/main/compare.png" width="700" height="500" />


   It is evident that despite having fewer parameters, the DenseNet model exhibits notably lower validation errors compared to the ResNet model, which also has an equal parameter count. These experiments were conducted with hyperparameters optimized for ResNet, as per the authors' configuration. However, the authors suggest that, with thorough hyperparameter tuning, DenseNet is expected to deliver even better performance.

My code defines a modified version of the ***DenseNet*** architecture, specifically the ***DenseNet-121*** variant.

Key Components of the Code:

1.**Input Layer**: The model starts with an input layer defined by *'self.inputs_1'*, which expects images of a specific input shape.

2.**Stages**:

-Stage 1: Initial convolutional layer followed by batch normalization and *'ReLU'* activation. It is followed by max-pooling.

-Stage 2: The first dense block, consisting of multiple dense layers with batch normalization, ReLU activation, and dropout. It's followed by a transition layer that reduces the spatial dimensions.

-Stage 3: The second dense block, followed by another transition layer.

-Stage 4: The third dense block, followed by another transition layer.

-Stage 5: The fourth dense block.

3.**Batch Normalization and ReLU** Activation: Batch normalization is applied before *'ReLU'* activation in most layers to improve training stability.

4.**Global Average Pooling**: After the last dense block, global average pooling is applied to reduce the spatial dimensions.

5.**Fully Connected Layer (Dense Layer)**: A dense layer is used for the final classification, where the number of neurons in the output layer matches the number of classes. This layer is followed by a *softmax* activation function for multi-class classification.

6.**Model Building**: The *tf.keras.Model* class is used to define the model's architecture, and the call method defines the forward pass of the model.

7.**Dense Block** : The dense_block function defines a block of densely connected layers. Each dense layer contributes to the growth of feature maps, promoting feature reuse.


 <img src="https://github.com/Mukhriddin19980901/DenseNet/blob/main/GIFS.gif" width="1000" height="500" />
 

8.**Transition Layer**: The transition_layer function reduces the spatial dimensions and complexity of feature maps by using *1x1* convolutions and average pooling.


<img src="https://github.com/Mukhriddin19980901/DenseNet/blob/main/transitionb.png" width="1000" height="500" />


9.**Dropout**: Dropout layers are included with configurable dropout rates to prevent overfitting.

10.**Regularization**: *L1* and *L2* weight regularization are applied to convolutional layers to help control overfitting.

**Usage**:

>You can create an instance of the DenseNet model by specifying the input shape and the number of output classes (in my case, 47). Once instantiated, you can build the model with a specific input shape and examine its summary.

>Overall, my code defines a deep neural network architecture that can be used for image classification tasks, and it incorporates many of the key features of the ***DenseNet*** architecture.
