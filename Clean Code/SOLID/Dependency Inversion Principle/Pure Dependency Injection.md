---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

Manually create all the dependencies injecting them explicitly.

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
