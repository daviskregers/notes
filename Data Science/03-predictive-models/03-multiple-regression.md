# Multiple regression

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/11-multiple-regression.ipynb

- What if more than one variable influences the one you're interested in?
- Example: predicting a price for a car based on it's many attributes (body style, brand, mileage, etc)
- If you also have multiple dependent variables - things you're trying to predict - that's a "multivariate regression"

### It sill uses least squares

- We just end up with coefficients for each factor.
    - For example, price $\alpha+\beta_1mileage + \beta_2age + \beta_3doors$
    - These coefficients imply how important each factor is (if the data is all normalized!)
    - Get rid of ones that doesn't matter!
- Can still measure fit with r-squared
- Need to assume the different factors are not themselves dependent on each other.
