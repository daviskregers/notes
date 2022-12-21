---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/single-responsibility-principle, review]
Review: Hard
---

# SRP Related patterns

- Applying the [[Single Responsibility Principle]] leads to appearance of many small [[class]]es
    - It is hard to understand the [[API]] of too many small classes
        - [[Facade design pattern]] may come to the rescue
        - Facades doesn't violate the [[Single Responsibility Principle]] since their responsibility is to bring the functionality required by a client together.

## Reasons for applying Facades

- Provide a simple [[API]] for client to interact with a set of complex objects
- Provide a cleaner [[API]] for client to interact with a poorly designed API

```csharp
namespace SOLID.SRP.Patterns
{
    class Problem
    {
        void Purchase()
        {
            int id = 123;
            Customer c = Customer.FindCustomer(id);

            int goodId = 13457;
            Order o = Stock.Find(goodId);
            CreditCardInfo cci = c.GetCreditCardInfo();
            BankGateway gateway = new BankGateway();
            gateway.ChargeCard(cci, o);

            c.AddToStatistics(o);
        }
    }

    class PurchaseFacade
    {
        public void ProcessPurchase(int customerId, int goodId)
        {
            Customer c = Customer.Find(Customer(customerId);
            Order o = Stock.Find(goodId);
            CreditCardInfo cci = c.GetCreditCardInfo();
            BankGateway gateway = new BankGateway();
            gateway.ChargeCard(cci, o);

            c.AddToStatistics(o);
        }
    }
}
```

## Related Patterns

- [[Facade design pattern]]
- [[Decorator design pattern]] - allows the [[behavior]] an individual object, either statically or dynamically, without affecting the behavior of other objects from the same [[class]].
- [[Composite design pattern]] - allows to compose objects into [[tree structure]]s to represent part-whole hierarchies, letting clients treat individual objects and compositions of objects uniformly.