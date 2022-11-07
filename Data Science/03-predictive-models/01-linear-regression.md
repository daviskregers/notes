# Linear regression

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/09-linear-regression.ipynb

- Fit a line to a data set of observations
- Use this line to predict unobserved values

## How does it work?

- Usually using "least squares"
- Minimizes the squared-error between each point and the line
- Remember the slope-intercept equation of a line? y=mx+b
- The slope is the correlation between the two variables times the standard deviation in Y, all divided by the standard deviation in X.
- The intercept is the mean of Y minus the slope times the mean of X
- But python will do all that for you.


There are more than one way to do it

- Gradient descent is an alternate method to least squares
- Basically iterates to find the line that best follows the contours defined by the data.
- Can make sense when dealing with 3D data.
- Easy to try in python and just compare the results to least squares
    - But usually least squares is a perfecly good choice.


### Measuring error with r-squared

- How do we measure how well our line fits our data?
- R-squared (aka coefficient of determination) measures:
    - The fraction of the total variation in Y that is captured by the model.

$$1.0-\frac{sum of squared errors}{sum of squared variation from mean}$$

### Interpreting r-squared

- Ranges from 0 to 1
- 0 is bad (none of the variance is captured), 1 is good (all of the variance is captured).
