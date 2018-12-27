# The Pipe operator

The pipe operator is used to setup a chain of method calls that pass results from one to other.

For example, we might have a function that uses 3 of the previously created methods:

```elixir
def create_hand(hand_size) do
    deck = Cards.create_deck
    deck = Cards.shuffle(deck)
    hand = Cards.deal(deck, hand_size)
end
```

This code contains repetitive code and can be refactored by using the pipe operator:

```elixir
def create_hand(hand_size) do
    Cards.create_deck
    |> Cards.shuffle
    |> Cards.deal(hand_size)
end
```

So the `create_deck` method is executed and fed into the `shuffle` method. The result of the `shuffle` method is fed into the `deal` method. Notice that the `deal` method accepts 2 arguments, only one is provided, it feeds the deck argument as well.

Provided this, it requires that you create methods with consistend arguments. If the method had different order of arguments like `hand_size` and then `deal`, it wouldn't know that.