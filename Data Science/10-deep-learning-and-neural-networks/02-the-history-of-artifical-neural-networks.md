# The history of artificial neural networks

## The biological inspiration

- Neurons in your cerebral cortex are connected via axons
- A neuron fires to the neurons it's connected to, when enough of it's input signals are activated.
- Very simple at the individual neuron level - but layers of neurons connected in this way can yield learning behavior.
- Billions of neurons, each with thousands of connections, yields a mind.

## Cortical columns

- Neurons in your cortex seem to be arranged in many stacks or columns that process information in parallel
- Mini-columns of around 100 neurons are organized into larger hyper columns. There are 100 million mini columns in your cortex
- This is coincidentally similar to how GPU's work

## The first artificial neurons

- Goes all the way back to year 1943.
- An artificial neuron fires if more than N input connections are active.
- Depending on the number of connections from each input neuron, and whether a connection activates or suppresses a neuron, you can construct AND, OR, or NOT logical constructs this way.

## The Linear Threshold Unit (LTU)

- Made in 1957
- Adds weights to the inputs, output is given by step function
- Sum up the products of the inputs and their weights.
- Output 1 if sum is >= 0

## The perceptron

- A layer of LTU's
- A perceptron can learn by reinforcing weights that lead to correct behavior during training
- This too has a biological basis (cells that fire together, wire together)

## Multi-layer perceptrons

- ADdition of "hidden layers"
- This is a deep neural network
- Training them is trickier

## A modern deep neural network

- Replaces step activation function with something better
- Apply softmax to the output
- Training using gradient descent
