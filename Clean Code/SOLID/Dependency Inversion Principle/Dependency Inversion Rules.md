---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---


- [[Dependency Inversion Principle]] implies that high-level policies should not depend on low-level details

- Two major types of dependencies: stable and unstable (or volatile)
    - Unstable dependencies are those to which we want to apply the inversion of control

- What [[Inversion Of Control (IoC)]] and [[Dependency Injection]] are and how they are related to the [[Dependency Inversion Principle]] and to each other

- 3 techniques of DI
    - [[Constructor Injection]], should be used 95% of the cases
    - [[Property Injection]]
    - [[Method injection]]

- Adhering to DIP leads to a [[plugin architecture]] which is known as the [[Ports and Adapters architecture]].
- There should be a single place which knows everything about application dependencies and their relationships and this is the [[Main partition]].
- Manual dependency injection may become tedious. That's why [[IoC-Container]]s exist, they help to simplify [[Dependency Injection]] in difficult cases.
