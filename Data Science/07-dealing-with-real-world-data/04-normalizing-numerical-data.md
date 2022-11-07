# Normalizing numerical data

## The importance of normalizing data

- If your model is based on several numerical attributes - are they comparable?
    - Example: ages mayrange from 0-100 and icomes from 0 to billions
    - Some models may not perform well when different attributes are on very different scales
    - It can result in some attributes counting more than others
    - Bias in the attributes can also be a problem

## Examples

- Scikit-learn's PCA implementation has a "whiten" option that does tihs for you. use it.
- Scikit-learn has a preprocessing module with hany normalize and scale functions
- Your data may have "yes" and "no" that needs to be converted to "1" and "0".

## Read the docks

- Most data mining and machine learning techniques work fine with raw, un-normalized data
- But double check the one you're using before you start
- Don't forget to re-scale your results when you're done.
