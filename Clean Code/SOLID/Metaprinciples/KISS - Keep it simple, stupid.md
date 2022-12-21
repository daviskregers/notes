---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

# KISS - Keep it simple, stupid

> "Make everything as simple as possible, but not simpler" - Alber Einstein

- [[Simplicity]] is a key goal in [[design]]
- [[YAGNI - You ain't gonna need it]] is about removing unnecessary code; KISS is about making the simplest implementation.

> A simple solution is better than a complex one, even if the solution looks stupid

### Achieving Simplicity

- Main technique is [[Decomposition]]
- Decomposition underlies all the [[SOLID Principles]]
- SOLID are aimed at achieving simplest solutions; Abusing SOLID leads to unnecessary [[complexity]] (Unity and Struggle of [[Opposites law]]).

- Prefer [[composition]] over [[inheritance]] where possible. Stick with if-else and switch-case statements until you see that you need to introduce polymorphism.
- Avoid [[preemptive optimization]]s. In 90% of cases slower solutions work enough fast. The exceptions: app main aspect of which is the performance.
- Smaller classes and smaller methods are better. The best method is a one-liner. [[Extract till you drop technique]].
- Don't rush to extract utility classes for private methods which are used from a single place within a class, leave it as it is until the other parts of code will require that method as well.
- Don't write [[parameterized general methods]], prefer methods which solve a specific problem.
- [[01-what-is-divide-and-conquer]]
- Strive to avoid [[comments]]
- Write [[prototype]]s and don't be afraid to throw them away
- Keep the number of entities which solve a problem roughly from 5 to 7
- Constantly work on simplifying your [[code base]]. This is the [[rule of a boy scout]].
- Keep the amount of optimized code closer to 5-10%

### Accidental & Essential Complexity

- [[Complexity]] imposed by the [[domain]] itself is called the "[[essential complexity]]"
- "[[Accidental complexity]]" is the complexity of our solutions which are intended to solve the problems of the domain.

### Simplicity

Two values of software:
- Correctness
- Good [[design]]
