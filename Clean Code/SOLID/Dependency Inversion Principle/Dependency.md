---
Created: 2022-12-22 10:47:29
Modified: Wednesday 16th November 2022 16:45:08
Type: course
Source: https://www.udemy.com/course/solid-principles/
Tags: [development/clean-code/solid/dependency-inversion-principle, review]
Review: Hard
---

## Types of Dependencies

- [[Framework]]
- [[3rd party library]]
- [[External system]] like [[File System]], [[Database]], Any [[system resource]].
- Dependency on a custom type built on top of the .NET framework

## Policy depends on Details

```
UI -> Person -> PersonRepository
```

- High-level objects of the domain layer directly depend on low-level objects of the infrastructural layer.
- It's hard to replace coupled dependencies.
- We can solve any problem by introducing an extra level of indirection

## Policy doesn't depend on Details

```
UI -> Person -> <interface> IPersonRepository <- PersonRepository
```

- IPersonRepository is a seam which inverts the dependencies.

# Volatile and Stable dependencies

- What dependencies should we abstract away?
    - Volatile dependencies
        - Dependency itself depends on the [[environment]] (web servers, db)
        - Dependency doesn't yet exist and is still under development
        - Dependency which is not installed on all machines of developers
        - Dependencies has a [[nondeterministic behaviour]] ([[randomizer]]s inside)
        - If none of these are true, a dependency is stable.
        - Volatile dependencies are those which we want to abstract away by introducing levels of indirection.
