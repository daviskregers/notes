---
Created: 2022-11-02 07:55:01
Modified: Tuesday 1st November 2022 07:54:51
Type: youtube
Source: https://www.youtube.com/watch?v=58jGpV2Cg50
Tags: [conspect, review]
Review: Hard
sr-due: 2022-11-04
sr-interval: 3
sr-ease: 252
---

[](https://www.youtube.com/watch?v=58jGpV2Cg50)[https://www.youtube.com/watch?v=58jGpV2Cg50](https://www.youtube.com/watch?v=58jGpV2Cg50)

![[ 3 Rules of TDD ]]

-   **Tests are the perfect ==documentation for developers==.**
-   **When you use tdd:**
    -   You cannot write code that's hard to write
    -   The code is automatically decoupled
    -   You trust the tests
-   **Separate logic from GUI**

 > Testing is like double-entry bookkeeping instead of assets and liabilities you have tests and production code. Instead of adding liabilities and assets and getting a 0, you get 0 failed tests.
 
-   **Inheritance** - test all the lines, each and every parent/child class.
-   **Mutation testing** - mutates code, expects failure. Makes sure tests actually make assertions.

- **TDD example:**
    -   Create a nothing() test that asserts that an empty test is working.
    -   Create a test that creates the class you are going to work with.
    -   Create the class.
    -   Assert it's empty
    -   Add push, assert it's not empty
    -   Add pop
    -   ... so on

-   Write tests around the solution first.
-   Use katas and tdd excercises to learn this.

> **Kent Beck's game** - write a failing test, try to make the code pass. If it doesn't - throw the code away and start over.

-   **There are two strategies to tdd** - outide-in (start with HTTP requests and go inwards, acceptance to unit) or inside-out (starts at the domain/business model and works it's way out to the api, unit to acceptance).

![[ Test Layers ]]

> Tests should not ==mirror== code ==(test class per production code class)==.