# SRP Related patterns

- Applying the SRP leads to appearance of many small classes
    - It is hard to understand the API of too many small classes
        - Facade design pattern may come to the rescue
        - Facades doesn't violate the SRP since their responsibility is to bring the functionality required by a client together.

## Reasons for applying Facades

- Provide a simple API for client to interact with a set of complex objects
- Provide a cleaner API for client to interact with a poorly designed API

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

## Related Patterns

- Facade
- Decorator - allows the behavior an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.
- Composite - allows to compose objects into tree structures to represent part-whole hierarchies, letting clients treat individual objects and compositions of objects uniformly.
