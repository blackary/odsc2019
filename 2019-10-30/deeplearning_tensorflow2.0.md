# Deep Learning (with TensorFlow 2.0)
## Dr. Jon Krohn
### 2019-10-30 9am-1pm

jonkrohn.com/talks
https://www.dropbox.com/s/r2fr16n1l4svo4x/ODSC-West_2019-10-30.pdf?dl=0 -- slides
github.com/jonkrohn/tf2 -- cloned as submodule

Notebooks can be used in colab, e.g. https://colab.research.google.com/github/jonkrohn/tf2/blob/master/notebooks/deep_net.ipynb

https://github.com/jonkrohn/DLTFpT/blob/master/installation/macOS.md --
instructions for installing dependencies in Docker

Simple cells - straight lines
Complex cells - corners and curves
More complex cells - more complex shapes
...
Final output

Traditional deep learning -- most time feature engineering, less time
modeling
Deep learning -- little time feature engineering, less time modeling

-- Is there a trade-off in performance across non-image tasks?

### Dense networks
- Full-connected -- each layer is densely-connected to each other layer

https://nbviewer.jupyter.org/ -- viewing shared jupyter notebook

Dense layers can only accept 1d inputs - so we collapse 28x28 grid into
1x784 array

Best practices - normalize - scale it down to 0-1 range before inputting

Copy of demo shallow_net notebook - https://colab.research.google.com/drive/13UF3kM9QpNMW11E9BM1g-40xBUAA0C_n#scrollTo=NotvM-cemd3m
- Simplest possible artificial neural network - 2 layers

"Loss" = difference between perfect answer and output

Convolutional layers -- can handle 2D & 3D inputs
Dense layers -- can only handle 1D inputs

Convolutional networks - usually a few convolutional layers, and then
a few dense layers

# Deep Learning Families

## Convolutional Neural Network
- Good at classifying images

## Recurrent Neural Networks
- Good at time-series data (e.g. stock prices, language translation)

## Generate Adversarial Networks -- two convolutional neural networks working against each other

- One = forger
- Two = detective

Both get better and better

whichfaceisreal.com

## Deep Reinforcement Learning
- Every decision you make impacts the world around it, so they are 
- Alpha Go -- netflix documentary

# Library options
- PyTorch and Keras are neck-and-neck, and TensorFlow is most popular in
  search popularity
- Keras is now a recommended requirement of TensorFlow 2.0

- Keras is a way of defining how to build models

Low-level Tensorflow is incredibly obtuse, so Keras makes it much easier

PyTorch is a complete re-write of the Torch library
- Feels the most pythonic
Other libraries were ported over to python from C, etc.

Tensorflow now has imperitive (eager) style, rather than symbolic style

Both TensorFlow and PyTorch have just-in-time version

"fast.ai abstracts too much, gives you too little control"

Tensorflow - "better for production deployment"

# Deep Learning Theory

Brain cell -- receives signals from 1000s of other cells
- Signals cause small + or - electric charge in the cell body
- If change is over a threshold, it sends an electrical signal ("action
  potential") down its axon

Perceptron -- simplest artificial neuron -- multiple inputs, single output
- Neuron itself does a calculation, based on the weights of each input
- Two parameters - weights and threshold

`Output = {1 if w * x + b > 0; 0 otherwise}`

Input later, "hidden layers", output layer

Dense network -- every neuron in a layer receives input from every neuron
in the previous layer

Input layer -- just a placeholder with a shape, doesn't do any computation

Output - y^ (hat) 

Perceptrons - only have binary inputs and outputs, we would like to have
continuous inputs/outputs
- Adjusting weights and biases will most of the time have no impact on the
  output -- 0 will stay 0, 1 will stay 1, only some times will it change
  at all

Activation function -- pass wx + b through this function to get
a continuous value
- Most popular activation function - sigmoid -- goes from 0 to 1, with
  mean of 0
- Sigmoid not used in hidden layers, because learning happens faster when
  the mean is closer to 0 -- related to partial derivatives
- More popular is now tanh (pronounced "tanch") -- goes from -1 to 1, mean
  of 0
- Most popular is Rectified Linear Unit (ReLU) -- max(0, z)
    - If z (`w*x + b`) < 0, just returns 0
    - if z >= 0, just returns z
- It's incredibly simple, but performs better than a curve
- Needs to be non-linear in hidden layer

Google "tensorflow keras activations"
- https://www.tensorflow.org/api_docs/python/tf/keras/activations
- Linear should only be used for output neurons where the goal is to get
  a continuous value, not a classification

Gradient descent -- used across ML models
- Can't use it on its own in Neural Networks, because of all the layers
- Backpropogation + Gradient Descent
- Allows the weights and biases to be learned backwards
- Weights and biases on output layer have the greatest impact on y-hat
- The more layers you have, the harder it is to train the earlier layers
- Practical limit -- maybe 1 or 2 dozen layers, before back-propogation
  stops working

## Your arsenal

*Neurons*
- sigmoid
- tanh
- ReLU

*Cost Functions*
- quadratic cost -- (sum of squares of differences) - Mean Squared Error
    - Why square? Makes cost positive, and quadratically penalizes errors
- cross-entropy -- good for classification

*Layers*:
- dense -- sends input to all neurons
- Softmax layer
    - Makes everything between 0 and 1, and sum to 1

*Initialization*
- Can't initialize weights to all be 0, because otherwise there will be no 
  variety
- Can't just use normal distribution, because you want to scale initial
  weight values based on how many inputs/outputs -- if it has more
  inputs/outputs, it should have a smaller weight

*Stochastic Gradient Descent*
- Split up training data into mini-batches (`batch_size=128` when fitting)
- Does gradient descent on each mini-batch
- Helps solve the problem of getting stuck in local minima
- May need to resample from less-popular classes, so that the distribution
  is the same (e.g. if most of the examples are negative, may need to
  over-sample from positive)
- Learning rate -- how big of a step to take
    - Don't really need to worry about the learning rate, because the
      learning rate can be adaptively learned by second-order algorithms,
      (e.g. Nadam) -- can vary across each parameter
    - With Nadam, the learning rate tends to be fast at the beginning, and 
      slows down as training goes on

*Avoiding Overfitting*
- Dropout - randomly remove some portion of neurons from a given layer
  during training
    - Prevents any given neuron from being too influencial, and memorizing
    - Especially important in later layers
    - At inference time, it uses all of the neurons again, but has to
      scale the weights
- Data Augmentation
    - Adding noise, rotation, etc.

http://playground.tensorflow.org/

*Deep learning network*
- Network with 3 or more hidden layers, so 5 layers total

Sequential in Keras -- the output from one layer flows immediately into
the next

https://colab.research.google.com/drive/1W6u6BZocKA6DYhnYygzR_Y7cNA9Mr6sS#scrollTo=GIVzBGIfEEfh

Can use pre-trained model as one of layers (e.g. a generalized image
classifier), and use transfer learning to use it for a more specific case

Hard limit on batch size -- how much memory you have on your machine
Recommended limit -- max of 128
