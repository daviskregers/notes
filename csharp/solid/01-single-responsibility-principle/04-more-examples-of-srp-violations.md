# More examples of SRP violations

```csharp
namespace SOLID.SRP.MoreExamples
{

    class Violation1
    {
        // example with business logic and formatting
        public string GetReport()
        {
            int clientsNumber = GetNumberOfClients();
            decimal totalIncome = GetTotalIncome()
            int satisfiedClients = GetSatisfiedClients();
            int unsatisfiedClients = GetUnsatisfiedClients();

            // ^ gather statistical data

            string clientsStr = $"Total number of Clients = {clientsNumber}";
            string incomeString $"Total Income = {totalIncome}";
            string satisfiedClientsStr = $"Number of satisfied clients = {satisfiedClients}";
            string unsatisfiedClientsStr = $"Number of unsatisfied clients = {unsatisfiedClients}";

            // ^ formatting

            return clientsStr + Environment.NewLine + incomeString +
                    Environment.NewLine + satisfiedClientsStr +
                    Environment.NewLine + unsatisfiedClientsStr +
                    Environment.NewLine;
        }
    }

    class Violation2
    {
        // example with business logic and changing the state - mechanics and policy
        public void FindAlarmDevice()
        {
            var driver = new AlarmDriver();
            string port = driver.Find();
            if (!string.IsNullOrWhiteSpace(port))
            {
                SystemState.AlarmCanBeUsed = false;
            }
            SystemState.AlarmCanBeUsed = true;
        }
    }

    class Violation3
    {
        // example with drawing - calculation coordinated, setting color and filling the rectangle
        // violation depends on actors
        public void DrawRectangle()
        {
            Rectangle rect = GetRectangle();
            Color color = Colors.Red;
            rect.Fill(color);
        }
    }
}
```

## Common SRP Violations

- Mixing logic and infrastructure
- A class or a module serves different layers
