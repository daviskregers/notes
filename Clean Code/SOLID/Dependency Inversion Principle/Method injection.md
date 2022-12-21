---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

Apply if only one method uses a [[Dependency]] or that dependency changes from one call to another.

```csharp
public interface ICurrencyRateProvider {
    int GetCurrencyRate(string currency);
}

public class PaymentService {
    public static Money CalculatePayment(ICurrencyRateProvider currencyRate) {
        return new Money();
    }
}
```

Pitfalls:
- [[Single Responsibility Principle]] violation
- [[IoC-Container]] doesn't inject dependencies into methods