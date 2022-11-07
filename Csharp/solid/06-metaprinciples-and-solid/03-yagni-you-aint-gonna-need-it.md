# YAGNI - You ain't gonna need it

- YAGNI is all about avoiding overengineering
- There is no a well-defined criterion to measure the "YAGNI-ness".
- "Always implement things when you actually need them, never when you just foresee that you need them" - Ron Jeffries


## Worse is Better

A model of software design and implementation which has the followin characteristics:
- Simplicity
- Correctness
- Consistency
- Completeness


        If you do something for a future need that doesn't actually increase the
        complexity of the software, then there's no reason to invoke YAGNI

## YAGNI

- Don't follow any principles blindly
- YAGNI depends on supporting practices, follow other practices such as Continous Integration, Refactoreing, Unit Testing as well.

## YAGNI Violation

- A team is working on a payment system which interoperates with many devices.
- Working on a current version, you need to implement a driver for interoperation with the model "Z" of a bill dispenser
- At the same time, a project manager expects that in four months they will need to support the "Y" model of a bill dispenser.

Deciding to implement such presumptive features is a classic violation of YAGNI principle!


    Useless Feature => all the efforts spent on analyzing, programming and testing.
    Useful Feature > stolen time + cost of carry + risk of wrong implementation

## YAGNI Violation 2

- You're writing a fuinction within a class which should parse a custom string.
    - Implemenmt that function right there, in that class
    - Implement that function and extract a utility class which contains that parsing function.

- Ask yourself if the function (or feature) is needed to be implemented right now
- If the answer is "yes", then implement it
- If the answer is "no", ask yourself another question
    - How much effort will it take to implement that function or featuyre in the future in case it will be required.
    - If the answer is "It will definitely be very simple" then keep all the things as they are, don't introduce anything additional.
    - If the answer is "It will take enormous amount of time to rewrite many things to tweak the design to make it enough supple to introduce that feature" - then consider performing some refactoring which will allow you to avoid massive rewriting in the future.

----

- You should always carefully plan the upcoming features
- No big upfront design
- The goal applying YAGNI is to save some time
- Perform refactoring to enable YAGNI
- Be ready to fail applying YAGNI
