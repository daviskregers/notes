---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/design-pattern, review]
Review: Hard
---

Converts the [[interface]] of a [[class]] into another [[interface]] clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces.

## Adapter example

```csharp
namespace SOLID.ISP
{
    public interface IWideInterface
    {
        void A();
        void B();
        void C();
        void D();
    }

    public interface INarrowInterface
    {
        void A();
        void B();
    }

    class Adapter : INarrowInterface
    {
        private readonly IWideInterface _wide;

        public Adapter(IWideInterface wide)
        {
            _wide = wide;
        }

        public void A()
        {
            _wide.A();
        }

        public void B()
        {
            _wide.B();
        }
    }

    class Client
    {
        private readonly INarrowInterface _narrow;

        public Client(INarrowInterface narrow)
        {
            _narrow = narrow;
        }
    }
}
```
