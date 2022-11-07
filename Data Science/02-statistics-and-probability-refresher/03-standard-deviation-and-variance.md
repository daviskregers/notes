# Standard Deviation and Variance

Python notebook https://github.com/daviskregers/data-science-recap/blob/main/02-standard-deviation-and-variance.ipynb

## Variance measures how "spread-out" the data is.

- Variance ($σ^2$) is simply the average of the squared differences from the mean.
- Example: What is the variance of the data set (1, 4, 5, 4, 8)
    - First find the mean $\frac{1+4+5+4+8}{5} = 4.4$
    - Now find the differences from the mean: (-3.4, -0.4, 0.6, -0.4, 3.6)
    - Find the squared differences: (11.56, 0.16, 0.36, 0.16, 12.96)
    - Find the average of the squared differences:
    - $σ^2 = \frac{11.56 + 0.16 + 0.36 + 0.16 + 12.96}{5} = 5.04$

## Standard deviation σ is just the square root of the variance

- $σ^2 = 5.04$
- $σ = \sqrt{5.04} = 2.24$
- So the standard deviation of (1, 4, 5, 4, 8) is 2.24
- This is usually used as a way to identify outliers. Data points that lie more than one standard deviation from the mean can be considered unusual.
- You can talk about how extreme a data point is by talking about "how many sigmas" away from the mean it is.

## Population vs Sample

- If you're working with a sample of data instead of an entire data set (the entire population)
    - Then you want to use the "sample variance" instead of the "population variance"
    - For N samples, you just divide the squared variances by N-1 instead of N.
    - So, in our example, we computed the population variance like this:
        - $σ^2 = \frac{11.56 + 0.16 + 0.36 + 0.16 + 12.96}{5} = 5.04$
    - But the sample variance would be:
        - $σ^2 = \frac{11.56 + 0.16 + 0.36 + 0.16 + 12.96}{4} = 6.3$
