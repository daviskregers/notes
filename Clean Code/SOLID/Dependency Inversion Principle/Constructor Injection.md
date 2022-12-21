---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

## Constructor Injection

- Protects the [[invariants]]
- Possible pitfall:
    - Tends to accumulate many [[Dependency|dependencies]]
        - smell of [[Single Responsibility Principle]] violation, consider extracting a class
    - Several [[Dependency|dependencies]] tend to be passed in together:

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

- 3rd party framework imposes a public [[default constructor]]

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
    - use [[Method injection]] instead