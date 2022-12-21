---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://refactoring.guru/refactoring
Tags: [development/clean-code/refactoring, review]
Review: Hard
---

# What is technical debt?

Technical debt is essentially unclean code. 

> If you get a loan from bank - you can purchase things faster, but you have to pay for it.
   You can rack up so much interest that the amount of the interest exceeds our total income, making full repayment impossible.

The same is with code. You temporarily speed up process without [[tests]].

## Causes

- **Business pressure.** Need to roll out features before they're finished.
- **Lack of understanding of the consequences of technical debt,**
- **Lack of tests.** Encourages quick but risky workarounds.
- **Lack of documentation.** Slows down introduction of new people to the project.
- **Lack of interaction between team members.** People working on an outdated understanding of processes.
- **Long-term simultaneous development in several branches.** The more changes made in isolation, the greater technical debt.
- **Delayed refactoring.** Requirements are constantly changing. The longer refactoring is delayed, the more dependent code will have to be reworked in future.
- **Lack of compliance monitoring.** Everyone writes code as they see fit.
- **Incompetence.**
