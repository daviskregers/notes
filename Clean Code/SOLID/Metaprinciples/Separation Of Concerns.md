---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

# SoC - Separation Of Concerns

- [[Single Responsibility Principle]] and SoC are strongly related
- Implies separation of different [[concern]]s in different modules
- Allows to build [[modular system]]s

Concerns we often face with:
- [[UI]]
- [[Business Logic]]
- [[Presentation Logic]]
- [[Database]]

---

## Leaking abstractions can ruin the SoC

presentation layer is bothered by [[UI]] concerns

```csharp
public Color TextColor
{
    get {
        bool result = Validate(text)
        return result ? Colors.Green : Colors.Red;
    }
}
```

[[Domain]] is bothered by [[Database]]:

```csharp
void DoWork(Customer customer1, Customer customer2)
{
    if (customer1.Id > 0) {
        // do something
    }

    if (customer1.Id == customer2.Id) {
        // do something
    }
}
```

---

- [[Layer]]s which represent different concerns should be isolated from each other in such a way that none of them should know a bout any intrinsic details of each other.
- [[SQL procedure]]s implementing [[business logic]] violate SoC but they're way much faster in certain scenarios.
