---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/liskov-substitution-principle, review]
Review: Hard
---


> If S is a subtype of T then objects of type T may be replaced with objects with type S, without breaking the problem.

The liskov Substitution states that [[Subtype]]s must be [[substitutable]] for their base types.

Example:
- Class called Client uses an interface B. Classes A and C inherit this interface. Class doesn't care if you pass in the class A or C since all it sees is interface B.

Duck typing in dynamic languages:
- If a bird swims like a duck, it quacks like a duck then I call that bird a duck.

Ways of breaking substitutability:
- Violating a [[Contract]]
- Violating [[Covariance]]/[[Contravariance]]

---

[[Contract]]
[[Liskov Substitution Principle Demo]]
[[Liskov Substitution Principle Violations]]
[[Liskov Substitution Princple Common Smells]]