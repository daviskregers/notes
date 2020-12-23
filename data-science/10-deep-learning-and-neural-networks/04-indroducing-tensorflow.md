# Introducing tensorflow

## Why tensorflow?

- It's not specifically for neural networks - it's more generally an architecture for executing a graph of numberical operations
- Tensorflow can optimize the processing of that graph, and distribute it's processing across a network
    - Sounds a lot like Apache Spark
- It can also distribute work accross GPUs
    - Can handle massive scale - it was made by Google
- Runs on about anything
- Highly efficient C++ code with easy to use Python APIs


## Tensorflow basics

- Install conda with `conda install tensorflow` or `conda install tensorflow-gpu`
- A tensor is just a fancy name for an array of matrix of values
- To use tensorflow you must
    - Construct a graph to compute your tensors
    - Initialize your variables
    - Execute that graph - nothing actually heppens until then

```python
import tensorflow as tf
a = tf.Variable(1, name="a")
b = tf.Variable(2, name"b")
f = a + b
tf.print(f)
```
## Creating a neural network with tensorflow

- Mathematical insights
    - All those interconeected arrows multiplying weights can be thought as a big matrix multiplication
    - The bias term can just be added onto the result of that matrix multiplication
- So in tensorflow, we can define layer of a neural network as

```python
output = tf.matmul(previous_layer, layer_weights) + layer_biases
```
- By using tensorflow directly we're kinda doing this the hard way.

---

- Load up our training and testing data
- Construct a graph describing our neural network
- Associate an optimizer (ie gradient descent) to the network
- Run the optimizer with your training data
- Evaluate your trained network with your testing data.

## Make sure your features are normalized

- Neural networks usually work best if your input data is normalized
    - That is, 0 mean and unit variance
    - The real goal is that every input feature is comparable in terms of magnitude
- ssikit_learn's StandardScaler can do this for you.
- Many data sets are normalized to begin with - such as the one we're about to use.
