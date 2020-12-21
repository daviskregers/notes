# Decision trees

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/16-decision-trees.ipynb

- You can construct a flowchart to help you decide a classification for something with machine learning
- This is called a decision tree
- Another form of supervised learing
    - Give if some sample data and the resulting classifications

## Example

- You want to build a system to filter out resumes based on historical hiring data
- You have a database of some important attributes of job candidates and you know which ones were hired and which ones weren't
- You can train a decision tree on this data, and arrive at a system for predicting whether a candidate will get hired based on it!

## How Decision Trees work

- At each step, find the attribute we can use to partition the data set to minimize the entropy of the data at the next step
- Fancy term for this simple algorithm: ID3
- It's a greedy algorithm - as it goes down the tree, it just picks the decision that reduce entropy the most at that stage.
    - That might not actually result in an optimal tree
    - It works

## Random forests

- Decision trees are very susceptible to overfitting
- To fight this, we can construct several alternate decision trees and let them "vote" on the final classification
    - Randomly re-sample the input data for each tree (fancy term for this: bootstrap aggregating or bagging)
    - Randomize a subset of the attributes each step is allowed to choose from
