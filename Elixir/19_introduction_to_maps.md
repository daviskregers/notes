# Introduction to maps

Maps are collections of key-value pairs. They are just like hashes in ruby, nearly identical to objects in javascript.

```elixir
iex(1)> colors = %{primary: "red", secondary: "blue"}
%{primary: "red", secondary: "blue"}
iex(2)> colors.primary
"red"
iex(3)> %{secondary: secondary_color} = %{primary: "red", secondary: "blue"}
%{primary: "red", secondary: "blue"}
iex(4)> secondary_color
"blue"
```

When we need to update a value in a map, we do not modify the map, we create a new one. 

```elixir
iex(1)> colors = %{primary: "red", secondary: "blue"}
%{primary: "red", secondary: "blue"}
iex(2)> Map.put(colors, :primary, "green")
%{primary: "green", secondary: "blue"}
```

This creates a new map with the updated value.

The second way to do this is:

```elixir
iex(1)> colors = %{primary: "red", secondary: "blue"}
%{primary: "red", secondary: "blue"}
iex(2)> %{ colors | primary: "green" }
%{primary: "green", secondary: "blue"}
```

This will only work when we are trying to update a property, if the property does not exist - it will throw an error.