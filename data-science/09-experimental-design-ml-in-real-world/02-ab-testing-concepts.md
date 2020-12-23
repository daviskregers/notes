# A/B Testiting concepts

## What is an A/B test?

- A controlled experiment, usually in the context of a website
- You test the performance of some change to your website (the variant) and measure conversion relative to your unchanged site (the control)

## What sorts of things can you test?

- Design changes
- UI flow
- Algorithmic changes
- Pricing changes
- You name it

## How do you measure conversion

- Ideally choose what you are trying to influence
    - Order amounts
    - Profit
    - Ad clicks
    - Order quantity
- But attributing actions downstream from your change can be hard
    - Especially if you're running more than one experiment

## Variance is your enemy

- Common mistake
    - Run a test for some small period of time that results in a few purchases to analyze
    - You take the mean order amount from A and B and declare victory or defeat
    - But, thereš so much random variation in order amounts to begin with that your result was just based on chance
    - You then fool yourself into thinking some change to your website, which could actually be harmful, has made tons of money.

- Sometimes you need to also look at conversion metrics with less variance
- Order quantities vs order dollar amounts for example
