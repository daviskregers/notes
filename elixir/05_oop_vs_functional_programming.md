# OOP vs functional programming

## Object Oriented Programming

In `OOP` approuch the code is organized into classes where each has has class has several methods. 

Each of these methods will operate on their local instance variables (properties).

For example of a deck of cards, there would be 2 classes - one will be `Deck` and one will be `Card`. The deck instance would hold a list of `Card` instances and provide several methods of managing them.

## Functional programming

In functional programming, the functions are organized into modules, there is no concept of a class or it's instance. 

The modules cannot be copied or instantiated, they are used only as collections of methods. 

For example, there might be a method in the `Cards` module that deals with shuffleing cards. It will accept input of list of strings that represent cards and return this list shuffled.