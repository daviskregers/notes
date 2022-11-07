---
Created: 2022-11-02 07:35:57
Modified: Tuesday 1st November 2022 07:35:47
Type: book | article | blog | etc
Source: source
Tags: [conspect, review, flashcards/cleancode/comments]
Review: Hard
sr-due: 2022-11-04
sr-interval: 3
sr-ease: 253
---

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/2a_ytyt9sf8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

- [x] Add flashcards / review ✅ 2022-11-01

-   **Comments**
    -   Most of the time comments are code smell
        -   They tend to compensate for bad code
        -   They deteriorate over time and can lie
        -   Most of the time are useless
    -   There really should be following comments:
        -   Legal / copyright comments
        -   Comments when you cannot use a more descriptive name due to a design pattern
        -   Hard to understand lines like regex query
    -   When writing comments
        -   Should reveal intent
        -   Are applied to local scope only
-   **Naming names**
    -   Should reveal intent
    -   Variable name length should be proportional to the scope that contains it.
    -   Function and class name length should be inverse proportional to the scope. The larger scope - the shorter it should be, more abstract.
    -   Avoid using names with "data", "info".

> Color comments red - read them - if useless, delete them.>

> Red column bar that shows you if you have too much of line-width.

---
flashcards

Why are comments considered a code smell?
?
- They tend to compensate for bad code
- They deteriorate over time and can lie
- Most of the time are useless
<!--SR:!2022-11-04,3,250-->

These are the comments that should be allowed:
?
- Legal / Copyright comments
- Comments when you cannot use a more descriptive name due to a design pattern
- Hard to understand lines like regex query
<!--SR:!2022-11-04,3,250-->

When writing comments you should:
?
- Reveal intent
- Apply them to the local scope only
<!--SR:!2022-11-04,3,250-->

Variable names should reveal ==intent==.
<!--SR:!2022-11-05,4,272-->

Variable name length should be ==proportional to the scope that contains it==.
<!--SR:!2022-11-05,4,272-->

Function and class name length should be ==inverse proportional to the scope. The larger scope - the shorter it should be, more abstract==.
<!--SR:!2022-11-05,4,272-->

Avoid using names with::"data", "info"
<!--SR:!2022-11-05,4,270-->