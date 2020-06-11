# DI Techniques

## Constructor Injection

- Protects the invariants
- Possible pitfall:
    - Tends to accumulate many dependencies
        - smell of SRP violation, consider extracting a class
    - Several dependencies tend to be passed in together:

```csharp
interface IDependency1 {}
interface IDependency2 {}
interface IDependency3 {}
interface IDependency4 {}

class ViewModel
{
    public ViewModel(   IDependency1 d1,
                        IDependency2 d2,
                        IDependency3 d3,
                        IDependency4 d4)
    {
    }
}
```

```csharp
class Infrastructure : IInfrastructure
{
    public Infrastructure(   IDependency1 d1,
                        IDependency2 d2,
                        IDependency3 d3,
                        IDependency4 d4)
    {
    }
}

class ViewModel
{
    public ViewModel(IInfrastructure infrastructure)
    { }
}
```

- Non-obligatory dependencies

```csharp
public class Customer {
    private ILogger _logger = new Logger();

    public Customer() {}
    public Customer(ILogger logger) {
        _logger = logger;
    }
}
```

- 3rd party framework imposes a public default constructor

```csharp
public class Customer {
    private ICustomerRepo _repo;

    // have to expose
    public Customer() {}

    public Customer(ICustomerRepo repo) {
        _repo = repo;
    }
}
```

- A certain dependency is used only in a single method
    - use method injection instead

## Property Injection

Exposes dependencies by using properties via getters and setters. Allows replacing
the dependency during the lifetime of the object.

The flexibility is a main advantage, but it should always be used only for optional dependencies.
It can easily break the encapsulation and make dependencies hidden.

Pitfalls:

- Breaks encapsulation

```csharp
public class Customer
{
    public Customer()
    {}

    public ILogger logger { get; set; } = new Logger();
}
```

## Method injection

Apply if only one method uses a dependency or that dependency changes from one call to another.

```csharp
public interface ICurrencyRateProvider {
    int GetCurrencyRate(string currency);
}

public class PaymentService {
    public static Money CalculatePayment(ICurrencyRateProvider currencyRate) {
        return new Money();
    }
}
```

Pitfalls:
- SRP violation
- IoC-Containers don't inject dependencies into methods
