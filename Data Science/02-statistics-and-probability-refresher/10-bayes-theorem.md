# Bayes' theorem

$$ P(A|B) = \frac{P(A)P(B|A)}{P(B)} $$

- The probability of A given B, is the probability of A times the probability of B given A over a probability of B.
- The key insight is that the probability of something that depends on B depends very much on the base probability of B and A.

## Examples

- Drug testing is a common example. Even a "highly accurate" drug test can produce more false positives than true positives.
- Let's say we have a drug test that can accurately identify users of a drug 99% of the time and accurately has a negative result for 99% of non-users. But only 0.3 of the overall population actually uses this drug.
- Event A - is a user of the drug, Event B - tested positively for the drug.
- We can work out from that information that P(B) is 1.3% (0.99 * 0.003 + 0.01 * 0.997) - the probability of testing positive if you don't)
- $P(A|B) = \frac{P(A)P(B|A)}{P(B)} = \frac{0.003*0.99}{0.013}=22.8%$
- So the odds of someone being an actual user of the drug given that they tested positive is only 22.8%
- Even though P(B|A) is high (99%), it doesn't mean P(A|B) is high.
