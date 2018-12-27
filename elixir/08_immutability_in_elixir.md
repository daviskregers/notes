# Immutability in elixir

When working with elixir, we never modify an existing data structure. 

For example, when passing a list of method, instead of modifying it, it creates a copy of it, modifies it and returns the copy. 

This concept is called `Immutability`.

So, in previous section, when calling the `shuffle` method on a deck. It doesn't actually shuffles the existing deck, it creates a copy of it and then shuffles it.