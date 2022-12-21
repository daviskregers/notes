---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/interface-segregation-principle, review]
Review: Hard
---

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

This will be refactored in [[Interface Segregation Principle Refactorings]]

---

# Demo of the 2nd problem

```csharp
namespace SOLID.ISP.Config
{
    public class Report
    {
        public string Generate()
        {
            return  $"Income:   {AppConfig.Config.Income}" + "\n" +
                    $"Expenses: {AppConfig.Config.Expenses}" + "\n" +
                    $"Total Revenue: {AppConfig.Config.TotalRevenue}";
        }
    }

    [DataContract(Namespace = "")]
    public class AppConfig
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

In this example we have a problem that we have a [[configuration class]] that acts as [[singleton]] and we have a report class that is closely tied to it. If we would want to test it, we couldn't use [[unit tests]], but only [[integration tests]].

To solve this, we can use an [[interface]] for this config class.

```csharp
namespace SOLID.ISP.Config
{
    public class Report
    {
        private readonly IAppConfig _appConfig;

        public Report(IAppConfig appConfig)
        {
            _appConfig = appConfig;
        }

        public string Generate()
        {
            return  $"Income:   {_appConfig.Config.Income}" + "\n" +
                    $"Expenses: {_appConfig.Config.Expenses}" + "\n" +
                    $"Total Revenue: {_appConfig.Config.TotalRevenue}";
        }
    }

    public interface IAppConfig
    {
        string ServerId { get; set; }
        string ServerIP { get; set; }
        string ServerPort { get; set; }
        int LoggingSwitch { get; set; }
        int AppSkinId { get; set; }
        decimal Income { get; set; }
        decimal Expenses { get; set; }
        decimal TotalRevenue { get; set; }
    }

    [DataContract(Namespace = "")]
    public class AppConfig : IAppConfig
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

Now we can introduce an [[unit test]]:

```csharp
using NUnit.Framework;

namespace SOLID.UnitTests
{
    [TestFixture]
    public class ReportTests
    {
        [Test]
        public void Generate_ValidInput_GeneratesReport()
        {
            IAppConfig appConfig = new TestableAppConfig()
            {
                AppSkinId = 0,
                Income = 10,
                LoggingSwitch = 1,
                Expenses = 100,
                ServerIP = "192.168.0.1",
                ServerId = "120888",
                ServerPort = "8080",
                TotalRevenue = 1000,
            };

            Report sut = new Report(appConfig);
            string report = sut.Generate();

            Assert.AreEqual(
                "Income: 10\n Expenses: 100\nTotal Revenue: 1000"
            report);
        }
    }

    public class TestableAppConfig : IAppConfig
    {
        string ServerId { get; set; }
        string ServerIP { get; set; }
        string ServerPort { get; set; }
        int LoggingSwitch { get; set; }
        int AppSkinId { get; set; }
        decimal Income { get; set; }
        decimal Expenses { get; set; }
        decimal TotalRevenue { get; set; }
    }
}
```

This is still not ideal, we need to set all the properties of the class even though
we don't actually use them. They can get added and we'll need to change the tests for them to work.