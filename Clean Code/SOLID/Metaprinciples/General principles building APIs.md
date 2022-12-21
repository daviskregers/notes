---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/metaprinciples, review]
Review: Hard
---

## API Intro
- [[API]] (Application Programming Interface) - set of functionality
- Types of APIs
    - [[Private API]] (zoo)
    - [[Public API]] (wilderness)
- Characteristics
    - [[Simplicity]]
        - Rule of thumb: "you can always add, but never remove".
        - Compromise between power and simplicity: when power of an API grows, it's simplicity degrades.
        - The only way to understand whether an API is simple or not is to estimate time spent on understanding by it's users.
    - Expressiveness and Compromises
        - Resources which can be allocated on API development are always limited
        - [[API]] it is almost impossible to create [[universal API]]s
        - [[API]] developers have to implement first things first
    - [[Extensibility]]
        - Reflects the capabilities to increase the power of an [[API]] without big rewrites
        - You should be able to add new functionality and preserve backwards compatibility
        - [[Open-Closed Principle]]
        - In [[public API]]s we should at first preserve the [[backwards compatibility]] (if any doubts regarding a new [[API member]] - don't introduce it)
    - [[Consitency]]
        - [[API]] has to be logical and consistent: design decisions - strongly opinionated!
        - Example of poor consistency in the PHP String library:
            - str_repeat
            - strcmp
            - str_cplit
            - strlen
            - str_word_count
            - strrev

## Public vs Private API

- The cost of bad decisions in public APIs may be extremely high
- Private APIs should be developed bearing in mind all API characteristics.
- Zookeepers must strive to become rangers.

## API Development principles

- APIs should be as simple as possible, but no simpler.
- A good API should allow to do a lot without learning a lot.
- APIs should be based on [[use case]]s.
    - Imagine that you're a client of that API
    - sketch API as soon as possible
- Provide low barrier for using an API.
    - In practice it means that you always:
        - Should provide the simplest constructors with default values of other required parameters.
        - Should throw [[exception]]s with messages which explain what to do to fix the problem.
        - Shouldn't require from clients to explicitly create more than one type for accomplishing main [[use case]]s.
        - Shouldn't require from clients to perform a [[wide initialization]] of an object.
- Build self-explanatory APIs
- Provide a decent [[documentation]]
