# Ensemble learning


- Random forests was an example of ensemble learning
- It just means we use multiple models to try and solve the same problem, and let them vote on the results.

- Random Forests uses bagging (bootstrap aggregating) to implement ensemble learning.
    - Many models are built by training or randomly-drawn subsets of the data.
- Boosting is an alternate technique where each subsequent model in the ensemble boosts attributes that address data mis-classified by the previous model
- A bucket of models trains several different models using training data and picks the one that works best with the test data
- Stacking runs multiple models at once on the data and combines the results together
    - This is how the netflix prize was won.

## Advanced Ensemble learning

- Bayes Optimal Classifier
    -  Theoretically the best - but always impractical
- Bayesian Parameter Averaging
    - Attemts to make BOC practical - but it's still misunderstood, susceptible to overfitting and often outperformed by the simpler bagging approach
- Bayesian Model Combination
    - Tries to address all of those problem
    - But in the end, it's about the same as using cross-validation to find the best combination of models
