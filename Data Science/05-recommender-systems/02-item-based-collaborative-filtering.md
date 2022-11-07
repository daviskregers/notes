# Item-Based Collaborative Filtering

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/20-item-based-movie-similarity.ipynb

- What if we based recommendations on relationships between things instead of people?
    - A movie will always be the same movie - it doesn't change.
    - There are usually fewer things than people (less computation to do)
    - Harder to game the system

---

- Find every pair of movies that were watched by the same person
- Measure the similarity of their ratings accross all users who watched both
- Sort by movie, then by similarity strength

(this is just one way to do it.)


