# Refactoring a better design

First we are creating an abstraction class for the payment model.


```csharp
namespace SOLID.SRP.Refactored
{
    public abstract class PaymentModel
    {
        protected TicketDetails _ticketDetails;

        protected PaymentModel(TicketDetails ticketDetails)
        {
            _ticketDetails = ticketDetails;
        }

        public abstract void BuyTicket();
    }
}
```

Then we are going to implement an interface for credit card payments.

```csharp
namespace SOLID.SRP.Refactored
{
    public interface ICanPayViaCreditCard
    {
        void Charge(TicketDetails ticketDetails, PaymentDetails paymentDetails);
    }
}
```

Then we are going to implement bank gateway interface

```csharp
namespace SOLID.SRP.Refactored
{
    public class BankGateway : ICanPayViaCreditCard
    {
        void Charge(TicketDetails ticketDetails, PaymentDetails paymentDetails)
        {
            // charge
        }
    }
}
```

Then we are implementing OnlinePayment class that derives the PaymentModel.

```csharp
namespace SOLID.SRP.Refactored
{
    private readonly PaymentDetails _payment;
    private readonly ICanPayViaCreditCard _bankGateway;


    public class OnlinePayment : PaymentModel
    {
        public OnlinePayment(TicketDetails ticketDetails, PaymentDetails paymentDetails) : base(ticketDetails)
        {
           _payment = payment;
           _bankGateway = new BankGateway();
        }
    }

    public override void BuyTicket()
    {
        _bankGateway.ChargeCard(base._ticketDetails, _payment);
    }
}
```

Then we are adding an interface for paying with cash.

```csharp
namespace SOLID.SRP.Refactored
{
    public interface ICanOperateWithCash
    {
        void AcceptCash();
        void DispenseChange();
    }
}
```

Then implement the inheritor for this interface:

```csharp
namespace SOLID.SRP.Refactored
{
    public class PosTerminalPayment: PaymentModel, ICanOperateWithCash
    {
        private readonly Action _onPayChangeToMobilePhone;
        private decimal _cashAccepted;

        public PosTerminalPayment(TicketDetails ticketDetails, Action onPayChangeToMobilePhone) : base(ticketDetails)
        {
            _onPayChangeToMobilePhone = onPayChangeToMobilePhone;
        }

        public override void BuyTicket()
        {
            AcceptCash();
            DispenseChange();
        }

        public void AcceptCash()
        {
            Random r = new Random();
            _cashAccepted = r.Next((int) _ticketDetails.Price, (int) _ticketDetails.Price + 1000);
        }

        public void DispenseChange()
        {
            if(_cashAccepted > _ticketDetails.Price && !TryToDispense())
            {
                _onPayChangeToMobilePhone?.Invoke();
            }
        }

        private bool TryToDispense()
        {
            // issue a command for dispensing
            return false;
        }
    }
}
```


// TODO: Closing notes
