# Deep Learning Details

## Backpropogation

- How do you train a MLP's weights? How does it learn?
- Backgropogation or specifically gradient descent using reverse-mode autodiff.
- For each training step
    - Compute the output error
    - Compute how much each neuron in the previous hidden layer contributed
    - Back-propogate that error in a reverse pass
    - Tweak wights to reduce the error using gradient descent

## Activation functions (aka rectifier)

- Step functions don't work with gradient descent - there is no gradient.
    - Mathematically they have no useful derivative.
- Alternatives
    - Logistic function
    - Hyperbolic tangent function
    - Exponential linear unit (ELU)
    - ReLU function (Rectified Linear Unit)
- ReLU is common. Fast to compute and works well.
    - Also, "Leaky ReLU", "Noisy ReLU"
    - ELU can sometimes lead to faster learning though.

## Optimization functions

- There are faster (as in faster learning) optimizers than gradient descent
    - Momentum optimization
        - Introduces momentum term to the descent, so it slows down as things start to flatten and speeds up as the slope is steep.
    - Nesterov Accelerated Gradient
        - A small tweak on momentum optimization - computes momentum based on the gradient slightly ahead of you, not where you are.
    - RMSProp
        - Adaptive learning rate tyo help point toward the minimum
    - Adam
        - Adaptive moment estimation - momentum + RMSProp combined
        - Popular choice today, easy to use


## Avoiding Overfitting

- With thousands of weights to tune, overfitting is a problem
- Early stopping (when performance starts dropping during training
- Dropout - ignore say 50% of all neurons randomly at each training step
    - Works surprisingly well
    - Forces your model to spread out it's learning


## Tuning your topology

- Trial & error is one way
    - Evaluate a smaller network with less neurons in the hidden layers
    - Evaluate a larger network with more layers
        - Try reducing the size of each layer as you progress - form a funnel
- More layers can yield faster learning
- Or just use more layers and neurons than your need, and don't care because your use early stopping
- Use "model zoos"
