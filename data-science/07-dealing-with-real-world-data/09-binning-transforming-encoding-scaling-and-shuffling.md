# Binning, Transforming, Encoding, Scaling and Shuffling

## Binning

- Bucket observations together based on ranges of values
- Example: estimated ages of people
    - Put all 20-somethings in one classification, 30-seomethings in other etc
- Quantile binning categorizes data by their place in the data distribution
    - Ensures even sizes of bins
- Transforms numeric data to ordinal data
- Especially useful when there is uncertainty in the measurements

## Transforming

- Feature data with an exponential trend may benefit from a logarithmic transform
- Applying some function to feature to make it better suited for training
- Example: YouTube recommendations
    - A numeric feature x is also represented by x^2 and sqrt(x)
    - This allows learning of super and sub-linear functions

## Encoding

- Transforming data into some new representation required by the model
- One-hot encoding
    - Create buckets for every category
    - The bucket for your category has a 1, all other have 0
    - Very common in deep learning, where categories are represented by individual output neurons.

![one-hot](img/one-hot.png)

## Scaling / normalization

- Some models prefer feature data to be normally distributed around 0 (most neural nets)
- Most models require feature data to at least be scaled to comparable values
    - Otherwise features with larger magnitudes will have more weight than they should
    - Example: modeling age and income as features - incomes will be much higher than ages
- Scikit-learn has a preprocessor module that helps (MinMaxScaler, etc)
- Remember to scale your results back up.

## Shuffling

- Many algorithms benefit from shuffling their training data
- Otherwiuse they may learn from residual signals in the training data resulting from the order which they were collected
