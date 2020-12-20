# Covariance and correlation

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/07-covariance-and-correlation.ipynb

![covariance](img/covariance.png)

## Covariance

- It measures how two variables vary in tandem for their means.

- Measuring covariance
    - Think of the data sets for the two variables as high dimensional vectors
    - Convert these to vectors of variances from the mean
    - Take the dot product (cosine of the angle between them) of the two vectors
    - Divide by the sample size

- Interpreting covariance is hard
    - We know a small covariance, close to 0, means there isn't much correlation between the two variables.
    - And large covariances - that is, far from 0 (could be negative for inverse relationships) mean there is a correlation.
    - Then the question is - how large does it have to be?

## Correltation

- Just divide the covariance by the standard deviations of both variables and that normalizes things.
- So a correlation results:
    - 0 means no correlation
    - 1 means perfect correlation
    - -1 means perfect inverse correlation

---

- Remember that correlation does not imply causation.
    - Only a controlled, randomized experiment can give you insights on causation.
    - Use correlation to decide what experiments to conduct!
