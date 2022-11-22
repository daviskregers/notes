---
Created: 2022-11-09 12:17:28
Modified: Tuesday 8th November 2022 12:17:10
Type: blog
Source: https://til.hashrocket.com/posts/63dvv2huk4-enable-gzip-for-all-phoenix-responses
Tags: [development/elixir/phoenix, review]
Review: Hard
sr-due: 2022-12-13
sr-interval: 21
sr-ease: 270
---

- [ ] Add flashcards / review 🛫 2022-11-24 ⏳ 2022-11-24 📅 2022-11-24

In `lib/myapp_web/endpoint.ex` change [[GZIP]] from `false` to `true`:

```elixir
 plug(Plug.Static, at: "/", from: :tilex, gzip: true, only: ~w(assets ...))
```

But why stop there? We can [[compress]] our dynamic document bodies just as easily. In `config/prod.exs`, add `compress: true` to the [[HTTP]] config of the [[endpoint]].

```elixir
config :my_app, MyAppWeb.Endpoint,
  http: [port: {:system, "PORT"}, compress: true]
```

---

Once done, you can validate that there is a `content-encoding: gzip` [[HTTP headers]] in the [[HTTP Response]].