---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/liskov-substitution-principle, review]
Review: Hard
---

# Contracts

- Programming to Contracts was elaborated by Bertrand Meyer
- "Object-Oriented Software Construction" by Meyer is recommended
- [[Eifel language]]

## What is Contract?

- Contracts have some [[semantic payload]]
- [[Interface]]s has no [[semantic payload]]s, they are not contracts

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
- [[Return value]]s or [[Return type]]s, and their meanings
- [[Error]] and [[exception]] condition values or types that can occur, and their meanings
- [[Side effect]]s
- [[Precondition]]s
- [[Postcondition]]s
- [[Invariant]]s

Example of [[Liskov Substitution Principle]] violation:
- Different [[return type]]s
- Different [[exception]]s
- [[unused argument]]s

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

## Code Contracts in [[Csharp]]

- You can write contracts in [[Csharp]] with a library called "[[Code Contracts]]". Harness the power of [[static code verification]] on correctness.
- [[Code Contracts]] library is not very popular though.
