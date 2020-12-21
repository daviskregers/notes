# Bayesian methods: Concepts

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/14-naive-bayes-spam-classifier.ipynb

## Remember Baye's theorem?

- $P(A|B) = \frac{P(A)P(B|A)}{P(B)}$
- Let's use it for machine learning! I want a spam classifier.
- Example: How would we express the probability of an email being spam if it contains the word "free"?
- $P(Spam|Free)=\frac{P(Spam)P(Free|Spam)}{P(Free)}$
- The numerator is the probability of a message being spam and containing the word "free" (this is subtly different from what we're looking for).
- The denominator is the overall probability of an email containing the word "free". (Equivalent to $P(Free|Spam)P(Spam) + P(Free|Not Spam)P(Not Spam)$)
- So together - this ratio is the % of emails with the word "free" that are spam.

### What about all the other words?

- We can construct $P(Spam | Word)$ for every meaningful word we encounter during training
- Then multiply these together when analyzing a new email to get the probability of it being spam.
- Assumes the presence of different words are independent of each other - one reason this is called "Naive Bayes".

### Sounds like a lot of work.

- Scikit-learn to the rescue!
- The CountVectorizer lets us operate on lots of words at once, and MultinomialNB does all the heavy lifting on Naive Bayes.
- We'll train it on known sets of spam and "ham" (non-spam) emails.

