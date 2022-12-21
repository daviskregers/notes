---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/liskov-substitution-principle, review]
Review: Hard
---

- Method throws [[NotSupportedException]]
- Empty or [[degenerative implementation]]
- [[Downcast]]s

## Tips

- [[Liskov Substitution Principle]] is often the result of [[Open-Closed Principle]] and [[Interface Segregation Principle]] violations

- If two [[class]]es share some logic and they are not substitutable
    - Create new [[base class]]
    - Inherit those two classes from a base class
    - Ensure that they are substitutable with the new base class
