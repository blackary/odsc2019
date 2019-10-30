# Deep Learning (with TensorFlow 2.0)
## Dr. Jon Krohn
### 2019-10-30 9am-1pm

jonkrohn.com/talks
https://www.dropbox.com/s/r2fr16n1l4svo4x/ODSC-West_2019-10-30.pdf?dl=0 -- slides
github.com/jonkrohn/tf2 -- cloned as submodule

Notebooks can be used in colab, e.g. https://colab.research.google.com/github/jonkrohn/tf2/blob/master/notebooks/deep_net.ipynb

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
