# Oauth on Phoenix

Elixir has a package `Ueberauth` that provides Oauth for phoenix. We will use github authentication strategy.

To install it, we add the dependencies to `mix.exs`:

```elixir
{:ueberauth, "~> 0.3"},
{:ueberauth_github, "~> 0.4"}
```

```elixir
def application do
    [mod: {Discuss, []},
     applications: [:phoenix, :phoenix_pubsub, :phoenix_html, :cowboy, :logger, :gettext,
                    :phoenix_ecto, :postgrex, :ueberauth, :ueberauth_github]]
  end
```

Next, well need to make a new OAuth application on github in [https://github.com/settings/applications/new](https://github.com/settings/applications/new).

As the `Authorization callback URL` we provide `http://localhost:4000/auth/github/callback`.

Then, we get a `Client ID` and `Client Secret` keys.

Add the following key to the `config/config.exs`.

```elixir
import_config "oauth.secret.exs"
```

Create `config/oauth.secret.exs` with following content:

```elixir
use Mix.Config

config :ueberauth, Ueberauth,
  providers: [
    github: { Ueberauth.Strategy.Github, [default_scope: "user"]}
  ]

config :ueberauth, Ueberauth.Strategy.Github.OAuth,
  client_id: "the_id",
  client_secret: "the_secret"
```

Now we add new routes:

```elixir

  scope "/auth", Discuss do
    pipe_through :browser

    get "/signout", AuthController, :signout
    get "/:provider", AuthController, :request
    get "/:provider/callback", AuthController, :callback
  end

```

Add User model by using `mix phoenix.gen.model User users email:string provider:string token:string`

It will generate the model as well as the migration.

And now, add the `web/controllers/auth_controller.ex`

```elixir
defmodule Discuss.AuthController do

  use Discuss.Web, :controller
  alias Discuss.User

  plug Ueberauth

  def callback(%{assigns: %{ueberauth_auth: auth}} = conn, _params) do
    # IO.inspect(conn)
    user_params = %{token: auth.credentials.token, email: auth.info.email, provider: "github"}
    changeset = User.changeset(%User{}, user_params)
    signin(conn, changeset)
  end

  defp signin(conn, changeset) do
    case insert_or_update_user(changeset) do
      {:ok, user} ->
        conn
        |> put_flash(:info, "Welcome back!")
        |> put_session(:user_id, user.id)
        |> redirect(to: topic_path(conn, :index))
      {:error, _reason} ->
        conn
        |> put_flash(:error, "Error signing in")
        |> redirect(to: topic_path(conn, :index))
    end
  end

  defp insert_or_update_user(changeset) do
    case Repo.get_by(User, email: changeset.changes.email) do
      nil ->
        Repo.insert(changeset)
      user ->
        {:ok, user}
    end
  end

  def signout(conn, _params) do
    conn
    |> configure_session(drop: true)
    |> redirect(to: topic_path(conn, :index))
  end

end
```
