# Regularization with Dropout and Early Stopping

## What is regularization?

- Prevents overfitting
    - Models that are good at making predictions on the data they were trained on, but not on new data it hasn't seen before
    - Overfitted models learned patterns in the training data that don't generalize to the real world
    - Often seen as high accuracy on training data set, but lower accuracy on test or evaluation data set.
        - When training and evaluating a model, we use training, evaluation and testind data sets.
- Regularization techniques are intended to prevent overfitting.


- One of regularization techniques is to simplify the model and use less layers, neurons.
- Another technique is to use Dropout. It removes some neurons at each network, it forces the NN to spread out it's learning.
- Early stopping. In the training process, when finishing the epoch, at some time we start to increasing the accuracy at the training data set, but the accuracy doesn't improve in the validation data set. It starts to overfit, we might want to stop the training process early.
