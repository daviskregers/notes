# Dependencies

## Types of Dependencies

- Framework
- 3rd party libraries
- External systems like File System, Database, Any system resource.
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
