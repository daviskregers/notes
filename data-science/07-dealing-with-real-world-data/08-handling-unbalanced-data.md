# Handling unbalanced data

## What is unbalanced data?

- Large discreptancy between "positive" and "negatrive" cases
    - i.e., fraud detection. Fraid is rate and most rows will be non-fraud.
- Mainly a problem with neural networks.


## Oversampling

- Duplicate samples from the minority class
- Can be done at random

## Undersampling

- Instead of creating more positive samples, remove the negative ones
- Throwing data away is usually not the right answer
    - Unless you are specifically trying to avoid "big data" scaling issues.

## SMOTE

- Synthetic minority over-sampling technique
- Artificially generate new samples of the minority class using nearest neighbors
    - Run KNN of each sample of the minority class
    - Create a new sample from the KNN result (mean of the neighbors)
- Both generates new samples and undersamples majority class
- Generally better than just oversampling


## Adjusting thresholds

- When making predictions about a classification (fraud / not fraud), you have some sort of threshold of probability at which point you'll flag something as the positive case (fraud).
- If you have too many false positives, one way to fix that is to simply increase that threshold.
    - Guaranteed to reduce false positives
    - But, could result in more false negatives
