# Phoenix

The Phoenix framework is one of the fastest frameworks available. It is built with the Elixir programming language and is used for building low-latency, fault-tolerant, distributed systems, which are increasingly necessary qualities for modern web applications.

## Generating a Phoenix project

```bash
mix phoenix.new discuss
```

Not modify the `mix.exs` file and add

```elixir
{:ecto_sql, "~> 3.0-rc.1"}
```

```bash
mix deps.get
mix ecto.create
```
Run the phoenix server with

```bash
mix phoenix.server
```

The project will be available at [http://localhost:4000](http://localhost:4000).

For interactive mode, you can run:

```bash
iex -S mix phoenix.server
```