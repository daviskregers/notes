# User-based collaborative filtering

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/19-movie-similarity-recommender-systems.ipynb

- build a matrix of things each user bought/viewed/rated
- Compute a similarity scores between users
- Find users similar to you
- Recommend stuff they bought/viewed/rated that you haven't yet.

## Problems with User-Based CF

- People are fickle, tastes change
- There are usually many more people than things - computationally more expensive than it should most of the time.
- People do bad things - easy to manipulate by creating fake personas on the platform.
