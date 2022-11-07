---
Created: 2022-11-02 08:05:37
Modified: Tuesday 1st November 2022 08:05:27
Type: youtube
Source: https://www.youtube.com/watch?v=sn0aFEMVTpA
Tags: [conspect, review, flashcards/cleancode/architecture]
Review: Hard
sr-due: 2022-11-04
sr-interval: 3
sr-ease: 251
---

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/sn0aFEMVTpA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

-   **Architecture**
    -   What is design and architecture?
        -   Roughly the same thing
    -   Goal: Minimize the human resources to build and maintain code.
    -   Quality can be measured in amount of effort to build something.
        -   If the effort increases - the design is bad.

What is the goal of an architecture?::To minimize the human resources to build and maintain code.
<!--SR:!2022-11-05,4,270-->

> Most startups fail because they can't maintain.

-   Slow & steady wins the race.
-   Over confidence that we will be able to clean up the mess later - that never happens.
-   Key to speed - not to slow down, in a steady, consistent and clean way.
-   TDD is always faster.
-   Solution: just be as clean as possible.

Software

-   Software must be changeable, changes must be cheap.
-   Software(does not work, changeable) > Software(works, not changeable)

![[ Clean architecture ]]

Change isolation:

-   Plugin to business rules
-   Plugin architecture

Frameworks:

-   not made for your benefit but for authors
-   decouple from frameworks
-   Look at the cost benefit when using them.