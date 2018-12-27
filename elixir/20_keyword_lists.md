# Keyword lists

Keyword lists is a merged structure between lists and tuples. 

```elixir
iex(1)> color = [{:primary, "red"}, {:secondary, "green"}]
[primary: "red", secondary: "green"]
```

To access the elements, you can use:

```elixir
iex(2)> color[:primary]
"red"
```

You can also use the following syntax:

```elixir
iex(3)> colors = [primary: "red", secondary: "green"]
[primary: "red", secondary: "green"]
```

