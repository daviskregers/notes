# Installing phoenix

The coure teaches phoenix v1.2 which can be installed by using the command

```bash
mix archive.install https://github.com/phoenixframework/archives/raw/master/phoenix_new-1.2.5.ez
```

The installation guide is available at [https://hexdocs.pm/phoenix/installation.html](https://hexdocs.pm/phoenix/installation.html).

Part from elixir, erlang and phoenix, we need node.js (>=5.0.0) too.

It can be installed using their website: [https://nodejs.org/en/](https://nodejs.org/en/).

As the last step, we need to install PostgreSQL datatabase server, the course has a guide on how to install it directly on the machine. 

I will be using docker for this.

```bash
docker run --name postgres -p 5432:5432 -e POSTGRES_PASSWORD=postgres -d postgres:11-alpine
```

Now you can connect on `localhost:5432` using user `postgres` and password `postgres`.

