---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

Exposes [[Dependency|dependencies]] by using properties via [[getters]] and [[setters]]. Allows replacing
the [[Dependency]] during the [[lifetime]] of the object.

The flexibility is a main advantage, but it should always be used only for [[optional dependencies]].
It can easily break the [[encapsulation]] and make dependencies hidden.

Pitfalls:

- Breaks [[Encapsulation]]

```csharp
public class Customer
{
    public Customer()
    {}

    public ILogger logger { get; set; } = new Logger();
}
```
