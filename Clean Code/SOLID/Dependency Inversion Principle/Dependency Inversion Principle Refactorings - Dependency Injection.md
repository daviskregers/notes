---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

We are refactoring [[Dependency Inversion Principle Demo]].

```csharp
public interface IFiscalRegistrator
{
    decimal GetSalesSum();
    decimal GetSumOfReturnedTickets();
}

public class FiscalRegistrator : IFiscalRegistrator
{
    public decimal GetSalesSum()
    {
        return 0;
    }

    public decimal GetSumOfReturnedTickets()
    {
        return 0;
    }
}

public interface IAccounter
{
    decimal GetSalesSum();
    decimal GetSumOfReturnedTickets();
}

public class Accounter : IAccounter
{
    public decimal GetSalesSum()
    {
        return 0;
    }

    public decimal GetSumOfReturnedTickets()
    {
        return 0;
    }
}

public class GainDivergenceChecker
{
    // public IAccounter Accounter { get; set; }
    // public IFiscalRegistrator Fr { get; set; }

    private IAccounter _privateAccounter;
    private IFiscalRegistrator _fr;

    public GainDivergenceChecker(IAccounter accounter, IFiscalRegistrator fr)
    {
        _privateAccounter = accounter;
        _fr = fr;
    }

    // public bool HasDivergence(IAccounter accounter, IFiscalRegistrator fr)
    public bool HasDivergence ()
    {
        return  accounter.GetSalesSum() == fr.GetSalesSum() &&
                accounter.GetSumOfReturnedTickets() == fr.GetSumOfReturnedTickets();
    }

    ...

}
```

Now we can write a test.

```csharp
using NUnit.Frakework;
using NUnit.Framework.Internal;

namespace SOLID.UnitTests
{
    [TestFixture]
    public class GainDivergenceCheckerTests
    {
        [Test]
        [TestCase(100, 100, 100, 100, true)]
        [TestCase(100, 200, 100, 200, true)]
        [TestCase(50, 100, 50, 100, true)]
        [TestCase(50, 100, 50, 50, false)]
        [TestCase(100, 100, 50, 50, false)]
        public void HasDivergence_ReturnsCorrectResult(
            decimal accounterSales, decimal accounterReturned,
            decimal frSales, decimal frReturned, bool expectResult
        )
        {
            IAccounter accounter = new TestableAccounter()
            {
                SalesSum = accounterSales,
                SumOfReturnedTickets = accounterReturned,
            };
            IFiscalRegistrator fr = new TestableFr()
            {
                SalesSum = frSales,
                SumOfReturnedTickets = frReturned,
            };

            var checker = new GainDivergenceChecker(accounter, fr);
            bool result = checker.HasDivergence();

            Assert.AreEqual(expectResult, result);
        }
    }

    public class TestableFr : IFiscalRegistrator
    {
        public decimal SalesSum { get; set; }
        public decimal SumOfReturnedTickets { get; set; }

        public decimal GetSalesSum()
        {
            return SalesSum;
        }

        public decimal GetSumOfReturnedTickets()
        {
            return SumOfReturnedTickets;
        }
    }

    public class TestableAccounter : IAccounter
    {
        public decimal SalesSum { get; set; }
        public decimal SumOfReturnedTickets { get; set; }

        public decimal GetSalesSum()
        {
            return SalesSum;
        }

        public decimal GetSumOfReturnedTickets()
        {
            return SumOfReturnedTickets;
        }
    }
}
```
