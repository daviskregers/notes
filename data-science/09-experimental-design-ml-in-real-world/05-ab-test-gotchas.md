# A/B test gotchas

## Correlation does not imply causation

- Even your low p-value score on well-designed experiment does not imply causation!
    - It could still be random chance
    - Other factors could be at play
    - It's your duty to ensure business owners understand this

## Novelty effects

- Changes to a website will catch the attention of previous users who are used to the way it used to be
    - They might click on something simply because it's new
    - But this attention won't last forever
- Good idea to re-run experiments much later and validate their impact
    - Often the "old" website will outperform the new one after a while, simply because it is a change

## Seasonal effects

- An experiment run over a short period of time may only be valid for that period of time
    - Example: Consumer behaviour near Christmas is very different that other times of year
    - An experiment run near christmas may not present behaviour during the rest of the year

## Selection Bias

- Sometimes your random selection of customers for A or B isn't really random
    - For example: assignments is based somehow on customer ID
    - But customers with low ID's are better customers than ones with high ID's
- Run an A/A test periodically to check
- Audit your segment assignment algorithms

## Data Pollution

- Are robots (both self-identified and malicious) affecting your experiment?
    - Good reason to measure conversion based on something that requires spending real money
- More generally, are outliers skewing the result?

## Attribution Errors

- Often there are errors in how conversion is attributed to an experiment
- Using a widely used A/B test platform can help mitigate that risk
    - If your is home-grown, it deserves auditing
- Watch for "gray areas"
    - Are you counting purchases toward an experiment within some given time frame of exposure to it? Is that time too large?
    - Could other changes downstream from the change you ŗe measuring affect your results?
    - Are you running multiple experiments at once?
