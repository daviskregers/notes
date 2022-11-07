# Phoenix plugs

There are 2 times of plugs - module plugs and function plugs. 

The module plugs are an actual module that has an init function and call function.

The function plugs is a function stored inside a controller.

Currently we have stored the user id in the session, but we have to check whether we are signed in. 

We can add a plug that helps with this authentication process by creating `web/controllers/plugs/set_user.ex` file.

```elixir
defmodule Discuss.Plugs.SetUser do

  import Plug.Conn
  import Phoenix.Controller

  alias Discuss.Repo
  alias Discuss.User

  def init(_params) do
  end

  def call(conn, _params) do
    user_id = get_session(conn, :user_id)

    cond do
      user = user_id && Repo.get(User, user_id) ->
        assign(conn, :user, user)
      true ->
        assign(conn, :user, nil)
    end

  end

end
```

And add it to the `web/router.ex`:

```elixir
plug Discuss.Plugs.SetUser
```

Now we can modify the `web/templates/layouts/app.html.eex`

and add right in the header

```html
<%= if @conn.assigns[:user] && @conn.assigns.user.id == topic.user_id do %>
    <div class="right">
        <%= link "Edit", to: topic_path(@conn, :edit, topic) %>
        <%= link "Delete", to: topic_path(@conn, :delete, topic), method: :delete %>
    </div>
<% end %>
```

We can add another plug to require authorized user:

```elixir
defmodule Discuss.Plugs.RequireAuth do

  import Plug.Conn
  import Phoenix.Controller

  alias Discuss.Router.Helpers

  def init(_params) do
  end

  def call(conn, _params) do

    if conn.assigns[:user] do
      conn
    else
      conn
      |> put_flash(:error, "You must be logged in.")
      |> redirect(to: Helpers.topic_path(conn, :index))
      |> halt()
    end

  end

end
```

And modify the TopicController:

```elixir
plug Discuss.Plugs.RequireAuth when action in [:new, :create, :edit, :update, :delete]
```


