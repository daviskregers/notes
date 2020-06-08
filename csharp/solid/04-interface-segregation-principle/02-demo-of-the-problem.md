# Demo of the problem

WPF APP -> Terminal1_COMServer
            -> BankTerminal1
        -> Terminal2_COMServer
            -> BankTerminal2
        -> Terminal3_COMServer
            -> BankTerminal3

```csharp
namespace SOLID.ISP
{
    public Interface IBankTerminal
    {
        void Start();
        void Stop();
        void Ping();
        void BankHostTest();
        void Purchase(decimal amount, string checkId);
        void CancelPayment(string checkId, decimal amount);
        void InterruptTransaction();

        event EventHandler<PaymentOperationCompletedEventArgs> PaymentCompleted;
        event EventHandler<PaymentOperationCompletedEventArgs> CancellationCompleted;
        event EventHandler<TransactionCompletedEventArgs> TransactionCompleted;

        bool IsContactReaderOnPort(string comPort);
        bool IsNonContactReaderOnPort(string comPort);
        string FindContactReader();
        string FindNonContactReader();
    }

    public class TransactionCompletedEventArgs : EventArgs {}

    public class ZapTerminal : IBankTerminal
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

        bool IsContactReaderOnPort(string comPort)
        {
            throw new NotImplementedException();
        }
        bool IsNonContactReaderOnPort(string comPort)
        {
            throw new NotImplementedException();
        }
        string FindContactReader()
        {
            throw new NotImplementedException();
        }
        string FindNonContactReader()
        {
            throw new NotImplementedException();
        }
    }

    public class PdqTerminal : IBankTerminal
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


}
```

The Zon terminal is a black box terminal that physically works on it's own credit card readers. Zon doesn't expose an API. The other 2 terminals doesn't take responsibility for reading cards automatically.

```csharp
namespace SOLID.ISP
{
    public class CardReadersCommunicatorViewModel
    {
        public CardReadersCommunicatorViewModel() {}
        public bool TestContactReaderOnPort(string port) { return false; }
        public bool TestNonContactReaderOnPort(string port) { return false; }
        public string FindContactReader() { return null; }
    }
}
```
