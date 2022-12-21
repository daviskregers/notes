---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/design-pattern, review]
Review: Hard
---

- There is an [[algorithm]] but small parts of the algorithm may vary.
- It defines the skeleton of an algorithm in an operation, deferring some steps to [[subclass]]es.
- Template method lets [[subclass]]es redefine certains steps of an algorithm without changing the algorithm's structure.

```csharp
namespace SOLID.OCP
{
    public abstract class PaymentProcessor
    {
        public void ProcessTransaction()
        {
            WithdrawMoney();
            CalculateBonus();
            SendGreetings();
        }
        protected abstract void WithdrawMoney();
        protected abstract void CalculateBonus();
        protected abstract void SendGreetings();
    }

    public class OnlineProcessor : PaymentProcessor
    {
        protected override void WithdrawMoney() {}
        protected override void CalculateBonus() {}
        protected override void SendGreetings() {}
    }

    public class PosTerminalProcessor : PaymentProcessor
    {
        protected override void WithdrawMoney() {}
        protected override void CalculateBonus() {}
        protected override void SendGreetings() {}
    }
}
```
