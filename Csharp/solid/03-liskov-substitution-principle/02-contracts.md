# Contracts

- Programming to Contracts was elaborated by Bertrand Meyer
- "Object-Oriented Software Construction" by Meyer is recommended
- Eifel language

## What is Contract?

- Contracts have some semantic payload
- Interfaces have no sementic payloads, they are not contracts

Example:

```csharp
public abstract class CollectionContract<T> : IList<T>
{
    public void Add(T item)
    {
        AddCore(item);
        count++;
    }

    public int Count
    {
        get { return count; }
    }

    protected abstract void AddCore(T item);
    private int count;

    ...
}
```

## What constitutes a method's contract?

- Acceptable and unacceptable input values or types, and their meanings
- Return values or types, and their meanings
- Error and exception condition values or types that can occur, and their meanings
- Side effects
- Preconditions
- Postconditions
- Invariants

Example of LSP violation:
- Different return types
- Different exceptions
- unused arguments

```csharp
public interface IBankTerminal
{
    int ProcessPayment(decimal amount, string uniqueId);
}

public class BenkTerminal1 : IBankTerminal
{
    private IBankTerminal1IPaymentGateway _gateway;

    // <returns> Response Code. Always >= 0</returns>
    public int ProcessPayment(decimal amount, string uniqueId)
    {
        // doesn't require uniqueId at all
        return (int)_gateway.ProcessPayment(amount);
    }

    public class BankTerminal2 : IBankTerminal
    {
        private IBankTerminal2IPaymentGateway _gateway;
        public int ProcessPayment(decimal amount, string uniqueId)
        {
            if(string.IsNullOrWhiteSpace(uniqueId))
            {
                throw new ArgumentException("A client must provide a unique ID or BankTerminal2");
            }

            return _gateway.ProcessPayment(amount, uniqueId);
        }
    }
}
```

## Code Contracts in C#

- You can write contracts in C# with a library called "Code Contracts". Harness the power of static code verification on correctness.
- Code Contracts library is not very popular though.
