# Mean, Median and Mode
TODO: link to notebook

## Mean

- Simply the average value
- Calculated - sum / number of samples
- Example:
    - Number of children in each house on my street
    - 0, 2, 3, 2, 1, 0, 0, 2, 0
    - The MEAN is $\frac{0+2+3+2+1+0+0+2+0}{9} = 1.11$

## Median

- Sort the values and take the value at the midpoint
- Example:
    - 0, 2, 3, 2, 1, 0, 0, 2, 0
    - Sort it:
    - 0, 0, 0, 0, 1, 2, 2, 2, 3
    -             ^ - 1


- If you have an even number of samples, take the average of the two in the middle.
- Median is less susceptible to outliers than the mean.
    - Example: mean household income in the US is $72,641, but the median is only $51,939 because the mean is skewed by a handful of billionaires.
    - Median better represents the "typical" american in this example.

## Mode

- The most common value in a data set
    - Not relevant to continuous numerical data
- Back to our number of kids in each house example
    - 0, 2, 3, 2, 1, 0, 0, 2, 0
    - 0: 4, 1: 1, 2: 3, 3: 1
    - The mode is 0
