# Elixir's relation with erlang

Elixir is not a standalone programming language. All the code that we write is not executed as elixir code.

The code that we write gets fed into `Elixir runtime` and is transpiled into `Erlang` which then compiles into something caled `BEAM` and executes it.

Erlang is a standalone programming language. It has different style of syntax than the elixir, but it has the same underlying concepts. 

Erlang was developed about 30 years ago for handling telecom networks. It is a wonderful language, but is notorious for it's hard to understand syntax. So, that is where `elixir` comes in. You can think of `elixir` as a dialect of `Erlang`, where you can get away from the annoying parts of `Erlang`.

The endproduct of is the `BEAM` which stands for `Bogdan/Björn's Erlang Abstract Machine`. It is a virtual machine where all the `Erlang` code is executed in. It's like the `JVM` in `Java.