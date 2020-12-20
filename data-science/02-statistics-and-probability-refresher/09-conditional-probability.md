# Conditional Probability

Python notebook: https://github.com/daviskregers/data-science-recap/blob/main/08-conditional-probability.ipynb

- If I have two events that depend on each other, what's the probability that both will occur?
- Notation: $P(A, B)$ is the probability of A and B both occuring
- $P(B|A)$ - probability of B given that A has occurred.

$$P(B|A) = \frac{P(A,B)}{P(A)}$$

## Example

- I give my students two tests. 60% of my students passed both tests, but the first test was easier. 80% passed that one. What percentage of students who passed the first test also the second one?

- A - passing the first test, B - passing the second test
- So we are asking for $P(B|A)$ - the probability of B given A
- $P(B|A) = \frac{P(A,B)}{P(A)} = \frac{0.6}{0.8} = 0.75$
- 75% of students who passed the first test passed the second as well.
