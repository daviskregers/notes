---
Created: 2022-11-08 08:36:20
Modified: Monday 7th November 2022 07:09:16
Type: course
Source: https://www.udemy.com/the-rust-programming-language-for-beginners/?xref=E0Aed11STH4LPUQvCz0GJFABTmM=
Tags: [development/rust, review]
sr-due: 2023-04-24
sr-interval: 145
sr-ease: 250
---

## Controlling visibility

When making a [[library]], usually we make a set of [[method]]s that users can use to do something. When we [[compile]] them, there will be a warning, that our project does not call them.

To prevent this, we can use the [[visibility keyword]] `pub`, which will mark it as a public [[API]].

```
pub fn connect() {}
```

