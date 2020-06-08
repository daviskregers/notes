# OCP Definition. Problem Statement

## Problem statement

- Software entities should be open for modification, but closed for modification.
    - When we need a change, we shouldn't dig deep into the system and change it
    - We should be able to introduce a change by adding new code instead of changing the existing one

Polymorphism is the answer to this problem.

## Why OCP?

- There is a high chance of introducing bugs during the modification process.
- It's hard to modify the behavior of an API which is already in use by many clients.

When customers ask for a new feature they think that feature will be added, they don't think that developers will modify anything.

We must modify the existing code if it contains a bug.

The protected variation pattern means the following:
- Identify points of predicted variation and create a stable interface around them.

## Demo of OCP violation

```csharp

public class BankTerminalFactory
{
    public static IBankTerminal CreateBankTerminal(BankTerminalModel model)
    {
        switch(model)
        {
            case BankTerminalModel.Brp;
                return new BrpTerminal();
            case BankTerminalModel.Dcp:
                return new DcpTerminal();
            default:
                throw new ArgumentException("Unknown model");
        }
    }
}
```

If we needed to add a new terminal type, we would need to change this existing code.

Whenever a software system must support a set of alternatives, one and only one module in the system should know their exhaustive list.

This can be solved by using Dependency Injection.
