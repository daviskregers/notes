# Identicon generation process

An indenticon is a 250x250px image which is splitted into a 5x5 grid - each 50x50px. The squares are mirrored around the center axis. The identicons are not generated randomly, but based on it's input.

So the Identicon generator will accept a string as an input, from it, will generate the identicon and save it as an image into a filesystem.

## The actual process of building an image

1. We take a string
2. Compute MD5 hash of the string
3. List of numbers based on the string
4. Pick color
5. Build grid of squares
6. Convert grid into image
7. Save image

## The process

We create a new project called `identicon`:

```bash
davis@davis-arch  ~/projects/elixir  mix new identicon
* creating README.md
* creating .formatter.exs
* creating .gitignore
* creating mix.exs
* creating config
* creating config/config.exs
* creating lib
* creating lib/identicon.ex
* creating test
* creating test/test_helper.exs
* creating test/identicon_test.exs

Your Mix project was created successfully.
You can use "mix" to compile it, test it, and more:

    cd identicon
    mix test

Run "mix help" for more commands.
```

Add the main method that will handle the input of the string. This main function will call all the necessary steps for the program.

Then we add a method called `hash_input` that handles the hashing the string and return it as a list of 16 numbers.

```elixir
   def hash_input(input) do
    :crypto.hash(:md5, input)
    |> :binary.bin_to_list
  end
```
The numerical values will range from `0-255` in this list, so we can use the first 3 values in the list to the next step - picking the color.

So the next step is to build a grid, which needs to be `5x5` and symetrical by the center axis.

```
1           2           3           2           1
4           5           6           5           4
7           8           9           8           7
10         11           12         11           10
13         14           15         14           13
```

Then apply each number in the list to a square. Color in the squares if the number is even, leave blank squares where number is odd.

We can use `struct` data structure in elixir to construct this grid. These are similar to maps, but they enforce that the only properties in the struct are previously defined.

By convention, if we previously know the properties of the data structure, we use a struct instead of a map.

To define a struct, we need to make a new module, so in the we create a new file called `lib/image.ex`.

In the struct, the list of numbers will be called `hex`.

```elixir
defmodule Identicon.Image do
    defstruct hex: nil
end
```
And we can modify the `hash_input` to return the struct instead.

```elixir
def hash_input(input) do
    hex = :crypto.hash(:md5, input)
    |> :binary.bin_to_list

    %Identicon.Image{hex: hex}
end
```

Now we implement the `pick_color` method. It will accept the `%Identicon.Image` struct.

```elixir
  def pick_color(image) do
    %Identicon.Image{ hex: [r, g, b | _tail] } = image
    %Identicon.Image{ image | color: {r,g,b} }
  end
```

We can refactor the code into a following structure:

```elixir
def pick_color(%Identicon.Image{ hex: [r, g, b | _tail] } = image) do
    %Identicon.Image{ image | color: {r,g,b} }
end
```

Now we implement the `build_grid` method which will chunk the input list by 3 elements and mirror the rows.

```elixir
  def build_grid(%Identicon.Image{hex: hex} = image) do
    grid = 
      hex
      |> Enum.chunk(3)
      |> Enum.map(&mirror_row/1)
      |> List.flatten
      |> Enum.with_index

    %Identicon.Image{ image | grid: grid }
  end

  def mirror_row(row) do
    [first, second | _tail] = row
    row ++  [second, first]
  end
```

The `&mirror_row/1` is a reference to a function `mirror_row`. 

The next step is to filter out the odd squares.

```elixir
  def filter_odd_squares(%Identicon.Image{grid: grid} = image) do
    grid = Enum.filtergrid, fn({code, _index}) -> 
      # calculate reminder by 2, if 0 - keep in list
      rem(code, 2)  == 0
    end

    %Identicon.Image{image | grid: grid}
  end
```

Now we can implement function for creating the actual image by using the `Erlang egd` since elixir itself does not provide any image manipulation libraries.

To install it, we add a dependency in `mix.exs`

```exlixir
{:egd, github: "erlang/egd"} 
```

Then restart the terminal and run the `iex -S mix`, it will ask for installing `rebar3`, accept and continue.

The first step is to create a pixel map for the for telling the `Erlang egd` how to draw the grid.

```elixir
  def build_pixel_map(%Identicon.Image{grid: grid} = image) do
    Enum.map grid, fn({_code, index}) ->
      horizontal = rem(index, 5) * 50
      vertical = div(index, 5) * 50
      top_left = {horizontal, vertical}
      bottom_right = {horizontal + 50, vertical + 50}

      {top_left, bottom_right}
    end
  end
```

And now, draw the image

```elixir
def draw_image(%Identicon.Image{color: color, pixel_map: pixel_map}) do
    image = :egd.create(250, 250)
    fill = :egd.color(color)

    Enum.each pixel_map, fn({start, stop}) ->
      :egd.filledRectangle(image, start, stop, fill)
    end

    :egd.render(image)
  end
```

Now create a method for saving into the filesystem

```elixir
def save_image(image, filename) do
    File.write("#{filename}.png", image)
  end
```

And bootstrap everything in the main function

```elixir
def main(input) do
    input
    |> hash_input
    |> pick_color
    |> build_grid
    |> filter_odd_squares
    |> build_pixel_map
    |> draw_image
    |> save_image(input)
  end
```

Now, we can run the `Identicon.main` and get the following images:

```elixir
Identicon.main("identicon")
```
![](../images/2018-12-27-22-04-01.png)

```elixir
Identicon.main("davis")
```
![](../images/2018-12-27-22-04-16.png)