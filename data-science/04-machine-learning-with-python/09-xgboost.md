# XGBoost

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/17-xgboost.ipynb

- stands for eXtreme Gradient Boosted trees
- Remember boosting is an ensemble method
    - Each tree boosts attributes that led to mis-classifications of previous tree
- It is amazing
    - routinely wins Kaggle competitions
    - Easy to use
    - Fast
    - A good choice for an algorithm to start with

## Features of XGBoost

- Regularized boosting (prevents overfitting)
- Can handle missing values automatically
- Parallel processing
- Can cross-validate at each iteration
    - Enables early stopping, finding optimal number of iterations.
- Incremental training
- Can plug in your own optimization objectives
- Tree pruning
    - Generally results in deeper, but optimized trees

## Using XGBoost
- pip install xgboost
- Also CLI, C++, R, Julia, JVM interfaces
- It's not just made for scikit_learn so it has it's own interface
    - Uses DMatrix structure to hold features & labels
        - Can create this easily from a numpy array though
    - All parameters passed via a dictionary
- Call train, then predict.

## XGBoost hyperparameters

- Booster
    - gbtree or gblinear
- Objective (ie multi:softmax, multi:softprob)
- Eta (learning rate - adjusts weights on each step)
- max_depth (depth of the tree)
- min_child_weight (can control overfitting, but too high will underfit)
- ... many others

It's almost all that you need to know for ML in practical terms, at least for simple classification or regression problems.
