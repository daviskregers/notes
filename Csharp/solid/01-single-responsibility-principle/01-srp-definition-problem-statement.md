# SRP Definition. Problem Statement

- Every object should have a single responsibility and that responsibility should be entirely encapsulated by the class.
- There should never be more than one reason for a class to change.

## Calculating Responsibilities

- Axis of changing requirements
    - If the class implements logging and caching on it's own - it has two responsibilities.
- API users are the source of changes
- The more responsibilities a class has, the more likely it's going to be changed.
- Applying SRP we want to separate different concerns
- SRP can be applied at different levels:
    - Function levels
    - Object level
    - Module

```csharp
{
    public class PaymentProcessor
    {
        public void Charge(decimal amount)
        {
            // initialize bank terminal
            // send a "Charge" request to the terminal
        }

        public string CreateReport()
        {
            // format a report
            return string.Empty;
        }

        public void PrintReport()
        {
            // initialize printer's driver
            // send a printing command
        }

        public void SavePayment()
        {
            // saving to DB
        }
    }
}
```

- The very first method `Charge` is responsible for dealing with a bank terminal. It needs to know how to initialize the connection and send proper commands.
- The `CreateReport` creates reports and needs to know how to format them properly.
- The `PrintReport` knows how to deal with printer's driver and send commands to it.
- The `SavePayment` deals with the database and saves the payment data.

- As we can see there are hidden responsibilities and we need a higher level object that orchestrates them.
- Classes with too many responsibilities are hard to understand
- When SRP is violated, responsibilities start to collate with each other. They become coupled.
- Gather all the same responsibilities together and separate from those what are different
- A set of functions or an interface is considered cohesive when each function is closely related to another.
- Coupling indicates how dependent modules are on the inner working of each other.
