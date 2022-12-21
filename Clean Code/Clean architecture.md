---
Created: 2022-11-02 08:05:37
Modified: Tuesday 1st November 2022 08:05:27
Type: youtube
Source: https://www.youtube.com/watch?v=sn0aFEMVTpA
Tags: [development/clean-code, conspect, review, flashcards/cleancode/architecture]
Review: Hard
sr-due: 2023-01-12
sr-interval: 56
sr-ease: 270
---

-   The [[web]] is a [[delivery mechanism]].
-   [[Architecture]] tells the intent of the application.
-   Use [[use case]]s. Use case - [[object]], [[interactor]]. Contains app-specific [[business rule]]s
-   user ↔ boundaries ← interactors → entities
-   [[MVC]] is real for small components like buttons etc not for pages.
-   [[Database]] should be treated as a [[IO device]].
    -   Implements [[Interface]], method or [[entity gateway]].
    -   Same thing with [[ORM]].
-   A good architecture allows you to defer until the last responsible moment.