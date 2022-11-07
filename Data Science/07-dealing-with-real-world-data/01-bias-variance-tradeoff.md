# Bias/Variance tradeoff

- Bias is how far removed the mean of your predicated values is from the real answer
- Variance is how scattered your predicted values are from real answer
- Describe the bias and variance of these four cases (assuming the center is correct)

![bias-variance](bias-variance.png)

Often you need to choose between bias and variance

- It comes down to overfitting vs underfitting your data.

But what you really case about is error
- Bias and variance both contribute to error
    - $error = bias^2 + variance$
- But it's error you want to minimize not bias or variance specifically
- A complex model wil have high variance and low bias
- A too-simple model will have low variance and high bias
- But both may have the same error - the optimal complexity is in the middle.

## Trying it to earlier lessons

- Increasing K in KNN decreases variance and increases bias (by averaging together more neighbors)
- A single decision tree is prone to overfitting - high variance
    -  But a random forest decreases that variance.


