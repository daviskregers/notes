# Measuring Entropy

- A measure of a data set's disorder - how same or different it is.
- If we classify a data set into N different classes (example: a data set of animal attributes and their species)
    - The entropy is 0 if all of the classes in that data are the same (everyone is an iguana)
    - - The entropy is high if they're all different

$$H(S) = -p_1 ln p_1 - ... - p_n ln p_n $$
- $p_i$ represents the proportion of the data labeled for each class.
- Each term looks like this.

![entropy-term](img/entropy-term.png)
