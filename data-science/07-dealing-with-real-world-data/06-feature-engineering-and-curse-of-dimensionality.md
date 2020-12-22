# Feature Engineering and Curse of Dimensionality

## What is feature engineering?

- Applying your knowledge of the data - and the model you're using - to create better features to train your model with.
    - Which  features should I use?
    - Do I need to transform these features in some way?
    - Should I create new features from the existing ones?
- You can't just throw in raw data and expect good results
- This is the art of machine learning; where expertise is applied
- "Applied machine learning is basically feature engineering" - Andrew Ng

## The curse of dimensionality

- Too many features can be a problem - leads to sparse data
- Every feature is a new dimension
- Much of feature engineering is selecting the features most relevant to the problem at hand
    - This often is where domain knowledge comes into play
- UNsupervised dimensionality reduction techniques can also be employed to distill many features into fewer features
    - PCA
    - K-means
