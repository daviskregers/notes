---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

This class uses 2 devices - accounter and fiscal registrator. These devices double
the operations that needs to be made so to validate that there are no mistakes.

This class checks whether there are any divergences between these 2 devices.

```csharp
namespace SOLID.DIP
{
    public class GainDivergenceChecker
    {
        private Accounter _privateAccounter;
        private FiscalRegistrator _fr;

        public gainDivergenceChecker()
        {
            _privateAccounter = new Accounter();
            _fr = new FiscalRegistrator();
        }

        public bool HasDivergence()
        {
            decimal salesSum = _privateAccounter.GetSalesSum();
            decimal sumOfReturnedTickets = _privateAccounter.GetSumOfReturnedTickets();

            decimal salesSumByFiscalRegistrator = _fr.GetSalesSum();
            decimal sumOfReturnedTicketsBytFiscalRegistrator = _fr.GetSumOfReturnedTickets();

            return  salesSum == salesSumByFiscalRegistrator &&
                    sumOfReturnedTickets == sumOfReturnedTicketsBytFiscalRegistrator;
        }

        private void ValidateDependencies(Accounter accounter, FiscalRegistrator fr)
        {
            if (accounter == null)
                throw new ArgumentNullException("accounter");
            if (fr == null)
                throw new ArgumentNullException("fr");
        }
    }

    internal class FiscalYearRegistrator
    {
        ...
    }

    internal class Accounter
    {
        ...
    }
}
```

If we wanted to add [[unit tests]] to this code, we couldn't really do that because it's tightly
coupled with the FiscalYearRegistrator and Accounter class.
