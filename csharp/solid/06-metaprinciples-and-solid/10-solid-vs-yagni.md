# SOLID vs YAGNI

- Fixing problems we ended up with more complex design
- Blind application of SOLID leads to needless complexity
- needless complexity often is the result of yagni violation

---

    "Developers have a tendency to attemt to solve specific problems with general solutions" - Greg Young


## Reused Abstraction Principle (RAP)

- RAP states that there should be at least three implementers on an interface or a base class (rule of three)
- Abstraction eliminates irrelevant and amplifies the essential

Basic algorithm:
- Start with a concrete implementation of a specific behavior
- Observe the emerging commonalities
- Apply the rule of three
