# Run dockerized phoenix in interactive mode

```
docker-compose run --service-ports app-phoenix bash
iex -S mix phx.server
recompile
```
