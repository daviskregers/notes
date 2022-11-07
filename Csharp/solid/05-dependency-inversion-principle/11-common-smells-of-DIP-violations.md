# Common smells of DIP violations

- A class explicitly creates one or more dependencies hiding them from a client
- A class uses non-deterministic dependencies like DateTime or Random
    - extract a class which works with non-deterministic dependencies and cover it by integration tests
    - create an adapter
- A class uses static dependencies, very often singletons

To remove the smells:
- Extract a later of indirection and make high-level policies independent of low-level details
- Adhere to the SRP
