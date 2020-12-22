# Understanding a confusion matrix

## Sometimes accuracy doesn't tell the whole story

- A test for a rare disease can be 99.9% accurate by just guessing "no" all the time.
- We need to understand true positives and true negative as well as false positives and false negatives.
- A confusion matrix shows this.

---

|               | Actual YES      | Actual NO       |
|---------------|-----------------|-----------------|
| Predicted YES | True positives  | False positives |
| Predicted NO  | False negatives | True negatives  |
