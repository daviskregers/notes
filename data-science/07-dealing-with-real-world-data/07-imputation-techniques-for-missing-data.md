# Imputation techniques for missing data

## Mean replacement

- Replace missing values with the mean value from the rest of the column (columns, not rows. A column represents a single feature.)
- Fast & easy, won't affect mean or sample size of overall data set.
- Median may be a better choice than mean when outliers are present
- But it's generally pretty terrible
    - Only works on column level, misses correlations between features
    - Can't use on categorical features (imputing the most frequent value can work in this case, thoough)
    - Not very accurate

## Dropping

- If not many rows contain missing data
    - And dropping those rows doesn't bias your data
    - And you don't have a lot of time
- But it's never going to be the right answer for the best approach.
- Almost anything is better. Can you substitute another similar fields perhaps? (i.e. review summary vs full text)

## Machine learning

- KNN: Find K nearest (most similar) rows and average their values
    - Assumes numerical data, not categorical
    - There are ways to handle categorical data (hamming distance), but categorical data is probably better served by
- Deep Learning
    - Build a machine learning model to impute data for your machine learning model.
    - Works well for categorical data. Really well, but it's complicated.
- Regression
    - Find linear or non-linear relationships between the missing feature and other features
    - Most advanced technique: MICE (Multiple Imputation by Chained Equations)

## Just get more data

- What's better than imputing data? Getting more real data!
- Sometimes you just have to try harder or collect more data.
