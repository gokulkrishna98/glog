---
layout: post
title:  "What is MLP ?"
date:   2024-03-07 19:35:37 -0500
categories: jekyll update
---

Multi Layer Perceptron  (MLP) is a one of the first deep learning neural networks (DNN).
These are really powerful and simple DNN. In this article, I will go through the science, the uses
and code a simple classification neural network using MLP.

## Setup
How do humans learn? We respond to problems in real world via our own representation of the world and its signals solve them
using brain. However, the computers are simple they just operate on numbers not on these raw signals efficiently (yet!).
So, What do you mean by machine learning if they cannot operate on these signals? 
It simply means to map certain numerical computation which solves the problem in real world. 
How do we do this ? We turn the real world to numbers and operate on them. For example, Images are turned 
into pixels which are set of numbers and textual sentences are turned into tokens which are numbers. 
Now let us create the setup. Say we have a real world problem (image classification), there is a input (image) we use brain and
write down what it is (text). Now, we turn this into a representation computers understand. Steps:
1. Convert Image into numbers (input)
2. Convert Output text into numbers (labels)
3. Find a relationship between them (machine learning)

Mathematical concept of functions is the axiom of machine learning, as they represent the relationship between 
a set of numbers to another set of numbers. Set of inputs is called domain and set of
outputs is called range. Say by magic (by human data labelling), we have a set of input and output pairs. We can clearly see that
it is impossible to predict the actual function from these samples, the best we can do is approximate this function.
How do we do this ? The best we can do is following :-
1. Randomnly (or heuristics) choose a family of function (polynomial, sin, exponential etc.)
2. Find all the functions that can map these input output pairs (space represented by training data). 
3. Now choose the best function among these set of functions.

Now the Step1 and Step2 are easy. Now how do we Step3 ? We use another function (objective function), that gives a score which 
is propotional to how good the function is. Usually this objective function is called loss, and we try to minimize this. Loss generally
implemented as distance between predicted value and actual value for a given input. To exploit the power of calculus, we limit ourselves to
continuos functions (in step1) and if the loss is also continous then the minimization problem can be solved by finding 
the gradient of loss and travel in the direction  where there minima. Learn about Gradient Descent (will post a link here in future).

Another important thing to know is that, any continuos function can be represented using polynomial functions (Taylor series approximation). 

At this point this setup seems so boring and meh. I said all that to tell how MLP belongs in this setup.
- MLP is one of the family of functions (Step1) we chose to solve a problem.
- This MLP usally represents a complex polynomial function (with activations) that can reprsent any continuos function across multiple dimensions.
- This implies MLP is continuous and we can find its gradient.
- We use gradients to minimize the loss in-turn find the best MLP parameters.


## How does this MLP Look ?
The image below is what MLP network looks like, but what the hell are these lines and nodes. What do
they represent ?
![mlp]({{site.baseurl}}/assets/images/mlp_image.jpg)
Let us list out the components which we see here:
- Nodes
- Edges
- Layer (input, hidden, output)

First let us go through the structure and the check out the concepts.

### Nodes
These are called neurons, similar to biological neuron, what do these neurons do.

![mlp_neuron](/assets/images/mlp_neuron.jpg)


