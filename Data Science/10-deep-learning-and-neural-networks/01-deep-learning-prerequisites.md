# Deep Learning Pre-Requisites

- Gradient descent requires knowledge of the gradient from your cost function (MSE)
- Mathematically we need the first partial derivative of all the inputs
    - This is hard and inefficient if you just throw calculus at the problem
- Reverse-mode autodiff can be used
    - Optimized for many inputs + few outputs (lika neuron)
    - Computes all partial derivatives in # of outputs + 1 graph traversals
    - Still fundamentally a calculus trick - it's complicated but it works
    - This is what tensorflow uses

## Softmax

- Used for classification
    - Given a score for each class
    - It produces a probability of each class
    - The class with the highest probability is the answer you get.
    - $$h_0(x) = \frac{1}{1+exp(-\theta^T x)}$$
    - x is a vector of input values, theta is a vector of weights.

## In review

- Gradient descent is an algorithm for minimizing error over multiple steps
- Autodiff is a calculus trick for finding the gradients in gradient descent
- Softmax is a function for choosing the most probable classification given several input types
