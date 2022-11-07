# Detecting outliers

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/25-dealing-with-outliers.ipynb

- Sometimes it's appropriate to remove outliers from your training data
- Do this responsibly! Understand why you are doing this.
- For example: in collaborative filtering a single user who rates thousands of movies could have a big effect on everyone else's ratings. That may not be desirable.
- Another example: in web log data, outliers may represent bots or other agents that shouldn't be discarded.
- But if someone really wants the mean income of US citizens for example, don't toss out billionaires just because you want to.

## Dealing with outliers

- Standard deviation provides a principled way to classify outliers.
- Find data points more than some multiple of standard deviation in your training data.
- What multiple? You just have to use common sense.
