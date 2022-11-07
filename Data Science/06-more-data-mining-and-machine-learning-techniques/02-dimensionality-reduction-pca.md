# Dimensionality reduction. Principal Component Analysis. (PCA)

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/22-principal-component-analysis.ipynb

## What is the curse of dimensionality?

- Many problems can be thought of as having a huge number of dimensions.
- For example, in recommending movies, the rating vector for each movie may represent a dimension - every movie is it's own dimension!
- Dimensionality reduction attemts to distill higher-dimensional data down to a smaller number of dimensions, while preserving as much of the variance in the data as possible.

---

- K-means clustering algorithm can be an example of dimensionality reduction algorithm. It reduces data down to K dimensions.

### Another  way: Principal Component Analysis (PCA)

- Involves fancy math - but at high level:
    - Finds "eigenvectors" in the higher dimensional data
        - These define hyperplanes that split the data while preserving the most variance in it
        - The data gets projected onto these hyperplanes, which represent the lower dimensions you want to represent
        - A popular implementation of this is called Singular Value Decomposition (SVD).
- Also really useful for things like image compression and facial recognition.


### Example: visualizing 4-D iris flower data

- The "Iris dataset" comes with scikit-learn
- An iris flower has petals and sepals (the lower, supportive part of the flower)
- We know the length and width of petals and sepals for many iris specimens.
    - That's four dimensions.
    - We also know the subspecies classification of each flower.
- PCA lets us visualize this in 2 dimensions instead of 4, while still preserving the variance.
