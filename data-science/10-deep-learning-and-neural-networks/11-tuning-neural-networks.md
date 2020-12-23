# Tuning Neural Networks: Learning Rate and Batch Size hyperparameters

## Learing Rate

- Neural networks are trained by gradient descent (or similar means)
- We start at some random point and sample different solutions (weights) seeking to minimize some cost function, over many epochs
- How far apart these samples are is the learning rate.

## Effect of learning rate

- Too high a learning rate means you might overshoot the optimal solution
- Too small learning rate will take too long to find the optimal solution
- Learning rate is an example of a hyperparameter

## Batch Size

- How many training samples are used within each epoch
- Somewhat counter intuitively:
    - Smaller batch sizes can work their way our of "local minima" more easily
    - Batch sizes that are too large can end up getting stuck in the wrong solution
    - Random shuffling at each epoch can make this look like very inconsistent results from run to run

## To Recap

- Small batch sizes tend to not get stuck in local minima
- Large batch sizes can converge on the wrong solution at random
- Large learning rates can overshoot the correct solution
- Small learning rates increase training time.
