# K-means clustering

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/14-naive-bayes-spam-classifier.ipynb

- Attempts to split data into K groups that are closest to K centroids
- Unsupervised learning - uses only the positions of each data point.
- Can uncover interesting groupings of people / things / behaviour
    - Example: Where do millionaires live?
    - What genres of music / movies / etc naturally fall out of data?
    - Create your own stereotypes from demographic data


## How it works

- Randomly pick K centroids (k-means)
- Assign each data point to the centroid it's closest to
- Recompute the centroids based on the average position of centroid's points
- Iterate until points stop changing assignment to centroids

If you want to predict the cluster for new points, just find the centroid they're closest to.

## Gotchas

- Choosing K
    - Try increasing K values until you stop getting large reductions in squared error (distances from each point to their centroids)
- Avoiding local minima
    - The random choice of initial centroids can yield different results
    - Run it a few times just to make sure your initial results aren't wacky
- Labeling the clusters
    - K-means does not attempt to assign any meaning to the clusters you find
    - It's up to you to dig into the data and try to determine that
