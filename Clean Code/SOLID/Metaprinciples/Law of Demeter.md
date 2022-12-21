---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

Law of Demeter (LoD) or principle of least knowledge is a [[design guideline]] for developing
software, particularly in [[Object Oriented Programming]].

Each unit should have only limited knowledge about other units - only other units "closely" related to the current unit.

Each unit should only talk to it's friends; not talk to strangers.

---

A method of an object may only call methods of:
- The [[object]] itself
- An [[argument]] of the [[method]]
- Any object created within the method
- Any direct properties/fields of the object

---

Let's pretend that we should model the business relationships between a paperboy and a customer who wants to buy magazines.

A paperboy rings the doorbell, a customer opens it. The paperboy somehow has to be paid and then hand over the magazine to the customer.

```csharp
namespace SOLID.DemeterLaw.Before
{
    public class Customer
    {
        public Customer(string firstName, string lastName)
        {
            FirstName = firstName;
            LastName = lastName;
            Wallet = new Wallet(1000m);
        }

        public string FirstName { get; }
        public string LastName { get; }
        public Wallet Wallet { get; }
    }

    public class Wallet
    {
        public Wallet(decimal moneyAmount)
        {
            MoneyAmount = moneyAmount;
        }

        public decimal MoneyAmount { get; private set; }

        public void AddMoney(decimal amount)
        {
            MoneyAmount += amount;
        }

        public void WithdrawMoney(decimal amount)
        {
            MoneyAmount -= amount;
        }
    }

    public class PaperBoy
    {
        public void DeliverMagazine(decimal costOfMagazine, Customer customer)
        {
            Wallet w = customer.Wallet;
            if (w.MoneyAmount > costOfMagazine)
            {
                w.WithdrawMoney(costOfMagazine);
            }
            else
            {
                // come back later
            }
        }
    }
}
```

We can improve this. This version better models the real world scenario. The paperboy doesn't have access to the wallet. The wallet class also now change and the paperboy is isolated from it.

```csharp
namespace SOLID.DemeterLaw.Before
{
    public class Customer
    {
        public Customer(string firstName, string lastName)
        {
            FirstName = firstName;
            LastName = lastName;
            Wallet = new Wallet(1000m);
        }

        public string FirstName { get; }
        public string LastName { get; }
        private readonly Wallet wallet;

        public decimal GetPayment(decimal amount)
        {
            if (wallet.MoneyAmount >= amount)
            {
                wallet.WithdrawMoney(amount);
                return amount;
            }
            return 0;
        }
    }

    public class Wallet
    {
        public Wallet(decimal moneyAmount)
        {
            MoneyAmount = moneyAmount;
        }

        public decimal MoneyAmount { get; private set; }

        public void AddMoney(decimal amount)
        {
            MoneyAmount += amount;
        }

        public void WithdrawMoney(decimal amount)
        {
            MoneyAmount -= amount;
        }
    }

    public class PaperBoy
    {
        public void DeliverMagazine(decimal costOfMagazine, Customer customer)
        {
            Wallet w = customer.Wallet;
            if (w.MoneyAmount > costOfMagazine)
            {
                w.WithdrawMoney(costOfMagazine);
            }
            else
            {
                // come back later
            }
        }
    }
}
```

---

The Law of Demeter is not about the number of dots.
This law is about reducing the [[coupling]] and improving the [[Encapsulation]].

It's OK to use many dots when digging the [[data structure]]s like:
- ExcelDocument.Sheet.Cell