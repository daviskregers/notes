---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/open-closed-principle, review]
Review: Hard
---

## Problem statement

- [[Software entities]] should be open for [[modification]], but closed for [[modification]].
    - When we need a change, we shouldn't dig deep into the system and change it
    - We should be able to introduce a change by adding new code instead of changing the existing one

[[Polymorphism]] is the answer to this problem.

## Why OCP?

- There is a high chance of introducing [[bug]]s during the modification process.
- It's hard to modify the behavior of an [[API]] which is already in use by many clients.

When customers ask for a new feature they think that feature will be added, they don't think that developers will modify anything.

We must modify the existing code if it contains a [[bug]].

![[Protected Variation Pattern]]

## Demo of OCP violation

```csharp

public class BankTerminalFactory
{
    public static IBankTerminal CreateBankTerminal(BankTerminalModel model)
    {
        switch(model)
        {
            case BankTerminalModel.Brp;
                return new BrpTerminal();
            case BankTerminalModel.Dcp:
                return new DcpTerminal();
            default:
                throw new ArgumentException("Unknown model");
        }
    }
}
```

If we needed to add a new terminal type, we would need to change this existing code.

Whenever a software system must support a set of alternatives, one and only one module in the system should know their exhaustive list.

This can be solved by using [[Dependency Injection]].

---

[[Open-Closed Principle Demo]]
[[Open-Closed Principle Refactorings]]
[[Open-Closed Principle Related Patterns]]
[[Open-Closed Principle Common Smells]]

![[Open-Closed Princple Rules]]

[[Open-Closed Principle vs YAGNI]]