---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/interface-segregation-principle, review]
Review: Hard
---

We can refactor the [[Interface Segregation Principle Demo]]

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

Then we can delete the unimplemented methods from the ZonTerminal and implement the [[interface]] in the other terminals.

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


---

We should segregate the configuration [[interface]]. The report class should only
know the configuration related to the reports.

```csharp
namespace SOLID.ISP.Config
{
    public class Report
    {
        private readonly IReportsConfig _reportsConfig;

        public Report(IReportsConfig reportsConfig)
        {
            _reportsConfig = reportsConfig;
        }

        public string Generate()
        {
            return  $"Income: {_reportsConfig.Income}" + "\n" +
                    $"Expenses: {_reportsConfig.Expenses}" + "\n" +
                    $"Total Revenue: {_reportsConfig.TotalRevenue";
        }
    }

    public interface IAppConfig
    {
        string ServerId { get; set; }
        string ServerIP { get; set; }
        string ServerPort { get; set; }
        int LoggingSwitch { get; set; }
        int AppSkinId { get; set; }
    }

    public interface IReportsConfig
    {
        decimal Income { get; set; }
        decimal Expenses { get; set; }
        decimal TotalRevenue { get; set; }
    }

    [DataContract(Namespace = "")]
    public class AppConfig : IAppConfig, IReportsConfig
    {
        private AppConfig(){...}

        [DataMember(IsRequired = true)]
        public string ServerId { get; set; }

        [DataMember(IsRequired = true)]
        public string ServerPort { get; set; }

        [DataMember(IsRequired = true)]
        public string LoggingSwitch { get; set; }

        [DataMember(IsRequired = true)]
        public int AppSkinId { get; set; }

        [DataMember(IsRequired = true)]
        public decimal Income { get; set; }

        [DataMember(IsRequired = true)]
        public decimal Expenses { get; set; }

        [DataMember(IsRequired = true)]
        public decimal TotalRevenue { get; set; }

        public static AppConfig Config { get; private set; }

        public static void Initialize()
        {
            using (Stream s = File.OpenRead("config.xml"))
            {
                Config = (AppConfig) new DataContractSerializer(typeof(AppConfig)).ReadObject(s);
            }
        }
    }

}
```
