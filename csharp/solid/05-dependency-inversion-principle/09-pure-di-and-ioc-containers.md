# Pure DI and IoC Containers

There are two ways of dealing with DI:

## Manually create all the dependencies injecting them explicitly - "Pure DI"

```csharp
class Program
{
    static void Main(string[] args)
    {
        var dependency1 = new Dependency1(...);
        var extension = "txt";
        var fileDateStore = new FileDateStore(dependency1, extension)
        ...
    }
}
```

## Use an IoC-Container (also known as DI-Container)

IoC-Container is a framework which helps to apply DI.
- Injects dependencies automatically
- Dependencies configuration
- Knows everything about dependencies
- IoC Container recursively creates all the required dependencies
