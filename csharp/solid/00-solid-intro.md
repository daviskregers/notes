# SOLID Intro

## What is design?

- Design of software is source code itself
- Architecture is the shape which code takes

- The source code specifies how software works
- Final product is a running program

## Building Software

- Big design upfront is very expensive in software development
- No guarantee that we take into account all the possible requirements
- Requirements tent to change very quickly
- Keep the design as clean as you can

## Design smells

- Rigidity
    - the cost of making a single change is very high.
    - Tight coupling between modules
- Fragility
    - Small changes in one module cause bugs appear in other modules
    - Tight coupling between modules
- Immobility
    - Component's can't be reused in other systems
    - Tight coupling between components
- Viscosity
    - Adding a single feature evotes dealing with tons of aspects
    - Tight coupling between components
- Needless complexity
    - Developers are tryting to forecast the future, introducing excessive points of extension
    - Developers should concentrate on the current requirements, constructing the supple architecture which can bend to meet new requirements

## Dependency management

- Most of the smells are caused by bad dependency management
- OO-languages can harness the power of dynamic dispatch
- Proper dependency management - key to a good architecture

## SOLID Principles

- SRP - Single Responsibility Principle
- OCP - Open/Closed Principle
- LSP - Liskov Substitution Principle
- ISP - Interface Segregation Principle
- DIP - Dependency Inversion Principle

These principles are not bound to any technology, you can apply them to any language.
SOLID is not a goal, it can't really be measured 
