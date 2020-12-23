# T-Tests and P-Values

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/30-t-tests-and-p-values.ipynb

## Determining significance

- So, how do we know if a result is likely to be real as opposed to just random variation?
- T-tests and p-values.

## The T-Statistic

- A measure of the difference between the two sets expressed in units of standard error
- The size of the difference relative to the variance in the data
- A high t value means there's probably a real difference between the two sets
- Assumes a normal distribution of behaviour
    - This is a good assumption if you're measuring revenue as conversion
    - See also: Fisher's exact test (for clicktrough rates), E-test (for transactions per user) and chi-squared test (for product quantities purchased)

## The P-value

- Think of it as the probability of A and B satisfying the "null hypothesis"
- So, a low P-value implies significance
- It's the probability of an observation lying at an extreme t-value assuming the null hypothesis

## Using P-values

- Choose some threshold for significance before your experiment
    - 1%? 5%?
- When your experiment is over:
    - Measure your P-value
    - If it's less than your significance threshold, then you can reject the null hypothesis
        - If it's a positive change, roll it out.
        - If it's a negative change, discard it before you lose more money.


