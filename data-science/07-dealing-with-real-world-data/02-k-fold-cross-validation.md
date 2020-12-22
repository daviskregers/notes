# K-fold cross validation to avoid overfitting

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/23-k-fold-cross-validation.ipynb

- One way to further protect against overfitting is K-fold cross validation
    - Split your data into K randomly assigned segments
    - Reserve one as your test data
    - Train on the combined remaining K-1 segments and measure their performance against the test set
    - Repeat for each segment
    - Take the average of the K r-squared scores
- Prevents you from overfitting to a single train/test split
