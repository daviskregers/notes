---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

Depependency Inversion Principle is a detailed version of [[Inversion Of Control (IoC)]]. Concretizes that "High-level modules should not depend on low level modules".

Dependency Inversion Principle is all about [[decoupling]].
- Coupling indicates how dependent modules are on the inner working of each other.
- Low coupling is often a sign of a well-structured computer system and a good [[Software Design]], and when combined with [[high cohesion]], supports the general goals of [[high readability]] and [[maintainability]].
- DIP is applicable both at the [[source code]] and [[binary level]]
- High-level modules should not depend on low-level modules. Both should depend on [[abstraction]]s.
- [[Abstraction]]s should not depend on details. Details should depend on abstractions.

```
Would you solder a lamp directly to the electrical outlet on your wall?
```

- You would only be able to use that socket for your lamp since they are tightly coupled.
- To fix the issue, we need to come up with a standard plug - then it can be plugged in the socket.


---

[[Dependency Inversion Principle Demo]]
[[Dependency Inversion Principle Refactorings - Dependency Injection]]
[[Dependency Investion Principle - Architectural implications]]
[[Dependency Inversion Principle Common Smells and Violations]]

![[Dependency Inversion Rules]]