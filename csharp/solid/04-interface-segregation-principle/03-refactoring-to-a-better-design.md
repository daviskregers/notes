# Refactoring to A better design

We can move the methods for the card reading from the IBankTerminal to a new interface.

```csharp
public interface IReadersCommunicable
{
    bool isContactReaderOnPort(string comPort);
    bool IsNonContactReaderOnPort(string comPort);
    string FindContactReader();
    string FindNonContactReader();
}
```

Then we can delete the unimplemented methods from the ZonTerminal and implement the interface in the other terminals.

```csharp

    public class ZapTerminal : IBankTerminal, IReadersCommunicable
    {
        private ZapTerminalServiceCommunicator _service = new ZapTerminalServiceCommunicator();
        public void Start() {}
        public void Stop() {}
        public void Ping() {}
        public void BankHostTest() {}

        event EventHandler<PaymentOperationCompletedEventArgs> PaymentCompleted;
        event EventHandler<PaymentOperationCompletedEventArgs> CancellationCompleted;
        event EventHandler<TransactionCompletedEventArgs> TransactionCompleted;

        bool IsContactReaderOnPort(string comPort)
        {
            return _service.IsContactReaderOnPort(comPort);
        }
        bool IsNonContactReaderOnPort(string comPort)
        {
            return _service.IsNonContactReaderOnPort(comPort);
        }
        string FindContactReader()
        {
            return _service.FindContactReader();
        }
        string FindNonContactReader()
        {
            return _service.FindNonContactReader();
        }
    }

    public class ZonTerminal : IBankTerminal
    {
        public void Start() {}
        public void Stop() {}
        public void Ping() {}
        public void BankHostTest() {}
        event EventHandler<PaymentOperationCompletedEventArgs> PaymentCompleted;
        event EventHandler<PaymentOperationCompletedEventArgs> CancellationCompleted;
        event EventHandler<TransactionCompletedEventArgs> TransactionCompleted;
    }

    public class PdqTerminal : IBankTerminal, IReadersCommunicable
    {
        private PdqTerminalServiceCommunicator _service = new PdqTerminalServiceCommunicator();
        public void Start() {}
        public void Stop() {}
        public void Ping() {}
        public void BankHostTest() {}
        event EventHandler<PaymentOperationCompletedEventArgs> PaymentCompleted;
        event EventHandler<PaymentOperationCompletedEventArgs> CancellationCompleted;
        event EventHandler<TransactionCompletedEventArgs> TransactionCompleted;

        bool IsContactReaderOnPort(string comPort)
        {
            return _service.IsContactReaderOnPort(comPort);
        }
        bool IsNonContactReaderOnPort(string comPort)
        {
            return _service.IsNonContactReaderOnPort(comPort);
        }
        string FindContactReader()
        {
            return _service.FindContactReader();
        }
        string FindNonContactReader()
        {
            return _service.FindNonContactReader();
        }
    }

    public class CardReadersCommunicatorViewModel
    {
        private readonly IReadersCommunicable _readersCommunicable;

        public CardReadersCommunicatorViewModel(IReadersCommunicable readersCommunicable)
        {
            _readersCommunicable = readersCommunicable;
        }

        public bool TestContactReaderOnPort(string port)
        {
            return _readersCommunicable.IsContactReaderOnPort(port);
        }

        public bool TestNonContactReaderOnPort(string port)
        {
            return _readersCommunicable.IsNonContactReaderOnPort(port);
        }

        string FindContactReader()
        {
            return _readersCommunicable.FindContactReader();
        }

        string FindNonContactReader()
        {
            return _readersCommunicable.FindNonContactReader();
        }
    }


}
```
