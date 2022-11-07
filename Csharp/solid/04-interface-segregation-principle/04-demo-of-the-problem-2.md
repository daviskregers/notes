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

In this example we have a problem that we have a configuration class that acts as singleton and we have a report class that is
closely tied to it. If we would want to test it, we couldn't use unit tests, but only integration tests.

To solve this, we can use an interface for this config class.

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

Now we can introduce an unit test:

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

In the next section we'll fix that using Interface Segregation.
