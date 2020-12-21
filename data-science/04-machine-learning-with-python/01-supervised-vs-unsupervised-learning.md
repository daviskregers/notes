# Supervised vs Unsupervised learning

## What is machine learning?

- Algorithms that can learn from observational data and can make predictions based on it. Pretty much what your own brain does too.

## Unsupervised learning

- The model is not given any "answers" to learn from. It must make sense of the data just given the observations themselves.
- Example: group (cluster) some objects together into 2 different sets. But I don't tell you what the "right" set is for any object ahead of time.

- Maybe you don't know what you're looking for - you're looking for latent variables.
- Example: clustering users on a dating site based on their information and behaviour. Perhaps you'll find there are groups of people that emerge that don't conform to your known stereotypes.
- Cluster movies based on their properties. Perhaps our current concepts of genre are outdated?
- Analyze the test of product descriptions to find the terms that carry the most meaning for a certain category.

## Supervised learning

- In supervised learing, the algorithm looks at the given observations and tries to predict the correct answers.
- The model created is then used to predict the answer for new, unknown values.
- Example: You can train a model for predicting car prices based on car attributes using historical sales data. That model can then predict the optimal price for new cars that haven't been sold before.

## Evaluating Supervised Learning

- If you have a set of training data that includes the value you're trying to predict - you don't have to guess if the resulting model is good or not.
- If you have enough training data, you can split it into two parts: a training set and test set.
- You then train the model using only the training set.
- And then measure (using r-squared or some other metric) the model's accuracy by asking it to predict values for the test set and compare that to the known, true values.

