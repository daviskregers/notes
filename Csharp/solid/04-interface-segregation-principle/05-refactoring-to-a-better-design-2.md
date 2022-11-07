# Refactoring to a better design. Example 2

We should segregate the configuration interface. The report class should only
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
