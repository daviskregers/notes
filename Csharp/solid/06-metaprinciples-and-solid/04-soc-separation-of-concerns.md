# SoC - Separation Of Concerns

- SRP and SoC are strongly related
- Implies separateion of different concerns in different modules
- Allows to build modular systems

Concerns we often face with:
- UI
- Business Logic
- Presentation Logic
- Database

---

## Leaking abstractions can ruin the SoC

presentation layer is bothered by UI concerns

```csharp
public Color TextColor
{
    get {
        bool result = Validate(text)
        return result ? Colors.Green : Colors.Red;
    }
}
```

Domain is bothered by Database:

```csharp
void DoWork(Customer customer1, Customer customer2)
{
    if (customer1.Id > 0) {
        // do something
    }

    if (customer1.Id == customer2.Id) {
        // do something
    }
}
```

---

- Layers which represent different concerns should be isolated from each other in such a way that none of them should know a bout any intrinsic details of each other.
- SQL procedures implementing business logic violate SoC but they're way much faster in certain scenarios.
