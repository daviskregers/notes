# Saving into filesystem

We can implement a saving method that saves the deck to the filesystem. 

```elixir
def save(deck, filename) do
    binary = :erlang.term_to_binary(deck)
    File.write(filename, binary)
end
```

The `:erlang` invokes an erlang method called `term_to_binary` which basically converts the `deck` into an object that can be written onto a filesystem.

![](../images/2018-12-27-15-49-45.png)

It saves it onto the filesystem in a binary mode.

![](../images/2018-12-27-15-50-57.png)