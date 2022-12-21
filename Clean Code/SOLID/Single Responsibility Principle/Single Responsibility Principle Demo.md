---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/single-responsibility-principle, review]
Review: Hard
---

# Demo of the problem

In this example we deal with an [[application]] that deals with buying tickets for trains.


```csharp
using System;

namespace SOLID.SRP.Violation
{
    public class PaymentModel
    {
        private decimal _cashAccepted;

        public void BuyTicket(  TicketDetails ticket,
                                PaymentDetails payment,
                                onPayChangeToMobilePhone)
        {
            if(payment.Method == PaymentMethod.CreditCard)
            {
                ChargeCard(ticket, payment);
            }
            else
            {
                AcceptCash(ticket);
                DispenseChange(ticket, onPayChangeToMobilePhone);
            }
        }

        private void ChargeCard(TicketDetails ticket, PaymentDetails payment)
        {
            var gateway = new ProcessingCenterGateway();
            gateway.Charge(ticket.Price, payment);
        }

        private void AcceptCash(TicketDetails ticket)
        {
            var r = new Random();
            _cashAccepted = r.Next((int) ticket.Price, (int) ticket.Price + 1000);
        }

        private void DispenseChange(TicketDetails ticket, Action onPayChangeToMobilePhone)
        {
            if(_cashAccepted > ticket.Price &&
                !TryToDispense(_cashAccepted - ticket.Price))
                    onPayChangeToMobilePhone?.Invoke();
        }

        private bool TryToDispense(decimal changeAmount)
        {
            return false; //or true
        }
}
```

This clearly violates [[Single Responsibility Principle]], there are two different payment methods that are coupled - paying with a credit card, cash.
It depends on PaymentDetails, TicketDetails, ProcessingCenterGateway.

```
PaymentDetails <-------------
    ^                       |
    |                       |
    |                       |
PaymentModel -----> ProcessingCenterGateway
    |
    |
TicketDetails
```

The [[refactoring]] to abide by the [[Single Responsibility Principle]] is viewed in [[Single Responsibility Principle Refactoring]].

More examples can be seen at [[Single Responsibility Principle Violations]].