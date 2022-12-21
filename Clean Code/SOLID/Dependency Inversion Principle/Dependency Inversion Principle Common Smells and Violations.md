---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

- A [[class]] explicitly creates one or more [[Dependency|dependencies]] hiding them from a client
- A class uses [[non-deterministic dependencies]] like [[DateTime]] or [[Random]]
    - extract a class which works with non-deterministic dependencies and cover it by integration tests
    - create an [[adapter]]
- A class uses [[static dependencies]], very often [[singleton]]s

To remove the smells:
- Extract a later of [[indirection]] and make high-level policies independent of low-level details
- Adhere to the [[Single Responsibility Principle]]
