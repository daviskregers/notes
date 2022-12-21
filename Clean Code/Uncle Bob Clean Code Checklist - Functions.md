---
Created: 2022-11-02 07:21:17
Modified: Tuesday 1st November 2022 07:18:05
Type: book | article | blog | etc
Source: source
Tags: [development/clean-code, conspect, review, flashcards/cleancode/functions]
Review: Hard
sr-due: 2022-12-12
sr-interval: 25
sr-ease: 259
---

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/7EmboKQH8lM" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

-   **Functions**
    -   Has same level of abstractions (high level abstractions and primitive structures together)
    -   Should follow the same methodology as news articles - the deeper you go into them, the more details you get.
    -   Should be small (usually 2-6 lines)
    -   Should do 1 thing - you cannot extract another function from it.
    -   Shouldn't have more than 1-2 indents
    -   Shouldn't have more than 3 arguments
    -   Shouldn't have bool input arguments
    -   Shouldn't have input arguments that are used as outputs
    -   Shouldn't contain switch/if-else statements (prefer [[polymorphism]], [[Open-Closed Principle]], [[NullObject]])
    -   Shouldn't have [[side-effects]] (file.open without close etc)
    -   Should have command/query separation. ([[Queries]] shouldn't modify the state[[,]] commands shouldn't return data).

Basically split your functions into more functions until you can't. Then probably you'll see hidden classes that you need to move these functions to. (Timestamp 1:00:23)

-   **Exceptions**
    -   Always prefer [[exceptions]] over [[error codes]]
    -   [[Function body]] should only contain [[try&catch block]] if there is one.
    -   Don't use nested try&catch blocks

---
Flashcards

- Has same level of ==abstractions (high level abstractions and primitive structures together)== together
<!--SR:!2022-11-04,3,250-->

- How big should an average function be::small (usually 2-6 lines)
<!--SR:!2022-12-25,32,270-->

- What should a function do?::It should do only 1 thing. You cannot extract another function from it.
<!--SR:!2023-02-15,84,292-->

- How many indents shouldn't the function exceed?::It shouldn't exceed 1-2 indents
<!--SR:!2022-12-26,33,282-->

- How many arguments should a function have::A functions shouldn't have move than 3 arguments
<!--SR:!2023-02-14,83,295-->

- A function shouldn't have ==boolean== input arguments
<!--SR:!2023-02-12,81,295-->

- A function shouldn't ==input== arguments that are used as ==outputs==.
<!--SR:!2022-12-29,36,282!2022-12-30,37,282-->

- A function shouldn't contain ==switch/if-else== statements. Prefer ==polymorphism, open-closed principle, null-object==.
<!--SR:!2022-12-31,38,275!2022-11-27,4,262-->

- A functions shouldn't have ==side==-effects like ==opening file without closing it==.
<!--SR:!2023-02-18,87,302!2022-11-26,3,264-->

- Functions should follow the ==command/query== seperation. ==Queries shouldn't modify the state, commands shouldn't return data==.
<!--SR:!2022-12-30,37,282!2022-11-26,3,264-->

- Always prefer ==exceptions== over error codes.
<!--SR:!2023-02-13,82,295-->

- Function body should only contain ==try&catch== block if there is one.
<!--SR:!2023-02-17,86,302-->

- Don't use nested ==try&catch== blocks.
<!--SR:!2023-02-16,85,301-->