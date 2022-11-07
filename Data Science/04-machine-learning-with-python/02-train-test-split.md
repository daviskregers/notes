# Train/test split

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/12-train-test-split.ipynb

## Train / test in practice

- Need to ensure both sets are large enough to contain representatives of all the variations and outliers in the data you care about
- The data sets must be selected randomly
- Train/test is a great way to guard against overfitting

## Train/test is not infallible

- Maybe your sample sizes are too small
- Or due to random chance your train and test sets look remarkably similar
- Overfitting can still happen

## K-fold Cross validation

- One way to further protect against overfitting is K-fold cross validation
- Sounds complicated, but it's not:
    - Split your data into K randomly assigned segments
    - Reserve one segment as your test data
    - Train on each of the remaining K-1 segments and measure their performance against the test set.
    - Take the average of the K-1 r-squared scores

