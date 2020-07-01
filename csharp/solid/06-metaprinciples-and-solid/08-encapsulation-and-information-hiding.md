# Encapsulation and information hiding

## Information hiding

- Information hiding is the principle of segregation, of the design decisions in a computer program that are most likely to change, thus protecting other parts of the program from extensive modification if the design decision is changed.
- Information hiding is the ability to prevent certain aspects of a class or software component from being accessible to it's clients, using either programming language features (like private variables) or an explicit exporting policy.

## Encapsulation

Encapsulation allows to reuse components without learning their internal details.

```csharp
class Customer {
    public event EventHandler<Customer> CustomerReceived;

    public Resuilt PaySalary(decimal amount)
    {
        return Result.Success();
    }

    public Maybe<Customer> GetCustomer(int id)
    {
        // get instance from DB
        var customer = new Customer();
        return Maybe<Customer>.From(customer);
    }

    public Result RemoveCustomer(int id)
    {
        return Result.Success();
    }
}
```
