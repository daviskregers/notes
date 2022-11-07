# Polynomial regression

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/10-polynomial-regression.ipynb

- Not all relationships are linear
- We can use higher orders of polynomials to produce more complex curves.

- First order: $y = mx + b$
- Second order: $y = ax^2 + bx + c$
- Third order: $y = ax^3 + bx^2 + cx + d$

## Beware of overfitting

- Don't use more degrees than you need to
- Visualize your data first to see how complex of a curve there might be
- Visualize the fit - is your curve going out of it's wat to accommodate outliers?
- A high r-squared simply means your curve fits your training data well, but it may not be a good predictor.
- Later we'll talk about more principled ways to detect overfitting (train/test)


