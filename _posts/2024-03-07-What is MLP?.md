---
layout: post
title:  "What is MLP ?"
date:   2024-03-07 19:35:37 -0500
categories: jekyll update
---

Multi-Layer Perceptron (MLP) stands as one of the pioneering architectures in deep learning neural networks (DNN). 
Renowned for its power and simplicity, MLPs have laid the foundation for many subsequent advancements in the field.
In this article, we delve into the science behind MLPs, explore their diverse applications, and walk through the 
process of coding a basic classification neural network using this influential architecture.

## Setup
How do humans learn? We tackle real-world problems by interpreting signals and information based on our own understanding of the world, using our brains to devise solutions. However, computers, while powerful, simply process numbers rather than raw signals efficiently (for now!). So, what exactly is meant by machine learning if computers cannot directly interpret these signals? Essentially, it involves mapping certain numerical computations to solve real-world problems. How do we achieve this? By translating real-world phenomena into numerical representations that computers can comprehend and manipulate. For instance, images are converted into pixels, essentially sets of numbers, while textual sentences are transformed into tokens, also represented by numbers. 

Let's set up a scenario: Imagine we have a real-world problem, such as image classification. We start with an input, say an image, and through cognitive processes, we identify and label what it represents. Next, we translate this human-generated understanding into a format understandable by computers. Here are the steps:

1. Convert the image into numbers (input).
2. Convert the output text into numbers (labels).
3. Establish a relationship between them through machine learning.

The mathematical concept of functions forms the foundation of machine learning, representing relationships between sets of numbers. The set of inputs is termed the domain, while the set of outputs is called the range. Suppose, by some magic, we acquire a set of input and output pairs. It becomes apparent that predicting the exact function from these samples is impossible; the best we can do is approximate it. How? Here's a simplified approach:

1. Randomly (or through heuristics), select a family of functions (e.g., polynomial, sine, exponential).
2. Identify all functions capable of mapping these input-output pairs (represented by the training data space).
3. Choose the best function from this set.

Steps 1 and 2 are relatively straightforward. But how do we tackle step 3? We employ another function, an objective function, which provides a score proportional to the function's effectiveness. This objective function, often called the loss, aims to minimize the discrepancy between predicted and actual values for a given input. Leveraging calculus, we limit ourselves to continuous functions in step 1. If the loss is also continuous, we can solve the minimization problem by computing the gradient of the loss and moving in the direction of its minimum. Learn about Gradient descent. 

An important concept to grasp is that any continuous function can be approximated using polynomial functions (Taylor series approximation). 

At this juncture, the setup may seem mundane, but it sets the stage for understanding how MLP fits into this framework:

- MLP is one of the families of functions (Step 1) we choose to solve a problem.
- Typically, an MLP represents a complex continuous function (involving dot producs to form another vector) with activations.
- This implies that MLP is continuous, and we can compute its gradient.
- We utilize gradients to minimize the loss, thereby identifying the best MLP parameters.

## How does this MLP Look ?
The image below depicts the structure of an MLP network, but to the uninitiated eye, the jumble of lines and nodes can seem perplexing. 
What exactly do these elements represent?

![mlp]({{site.baseurl}}/assets/images/mlp_image.jpg)

Let's break down the components visible in the image:
- Edges: These are the lines connecting various nodes in the network.
- Neuron: Each circle or node represents a neuron in the network.
- Layers: The network comprises different layers, including input, hidden, and output layers.
Now, let's delve into the structure and concepts underlying these components.

### Edges/Connections
The edges within this network symbolize numerical values, serving as representations of real-world problems that the network operates upon. These numerical representations can take various forms, but for simplicity, let's consider them as numbers. Each node in the layerr forms a set of numbers, a vector. This vectorization facilitates efficient computation during inference.

When each neuron is connected to every other neuron in the subsequent layer, we refer to this arrangement as a fully connected layer.

### Nodes
These units are termed neurons, akin to their biological counterparts. But what exactly do they do?

Each neuron stores a numerical value for every input connection it receives. Consequently, every neuron possesses a set of these numbers, which collectively form vectors known as the neuron's weights. One can think of these weights as reflecting the importance that each input holds for the neuron. To compute an output from the neuron, we perform a weighted sum of the input values by multiplying them with their corresponding weights and then adding them together. In essence, this operation boils down to the vector dot product between the input vector (formed by the input connections) and the weight vector.

To imbue neurons with greater expressive power, we introduce an activation operation on the output. This activation operation introduces non-linearity, expanding the repertoire of functions that the neurons can represent.

### Bias
We include a bias number for each neuron because it acts as a reference point from which learning can commence. If we were to initialize all weights to zero, the network would encounter difficulties in learning. Alternatively, utilizing random initialization introduces inherent bias, providing the network with diverse starting conditions essential for effective learning.

### Layer
We can observe that neurons can be grouped based on their positional similarity within the network. The layer that directly receives input numbers is termed the input layer, while the layer responsible for outputting the predicted values is referred to as the output layer. In contrast, the intermediate layers lack any direct physical interpretation. Instead, they represent mappings of intermediate functions within the numerical space. Consequently, these layers are termed hidden layers.

![mlp_neuron]({{site.baseurl}}/assets/images/mlp_neuron.jpg)

## Application of MLP



