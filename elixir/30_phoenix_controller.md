# Phoenix controller

The controllers are located in `web/controllers` directory.

We can create a new controller controller by adding `web/controllers/topic_controller.ex`

With following content.

```elixir
defmodule Discuss.TopicController do

  use Discuss.Web, :controller
  alias Discuss.Topic

  def index(conn, _params) do
    render conn, "index.html", topics: Repo.all(Topic)
  end

  def show(conn, %{"id" => topic_id}) do
    render conn, "show.html", topic: Repo.get!(Topic, topic_id)
  end

  def new(conn, _params) do
    changeset = Topic.changeset(%Topic{}, %{})
    render conn, "new.html", changeset: changeset
  end

  def create(conn, %{"topic" => topic}) do

    changeset = Topic.changeset(%Topic{}, topic)

    case Repo.insert(changeset) do
      {:ok, _post} ->
        conn
          |> put_flash(:info, "Topic created")
          |> redirect(to: topic_path(conn, :index))
      {:error, changeset} ->
        render conn, "new.html", changeset: changeset
    end

  end

  def edit(conn, %{"id" => topic_id}) do
    topic = Repo.get(Topic, topic_id)
    changeset = Topic.changeset(topic)
    render conn, "edit.html", changeset: changeset, topic: topic
  end

  def update(conn, %{"id" => topic_id, "topic" => topic}) do

    changeset = Repo.get(Topic, topic_id)
      |> Topic.changeset(topic)

    case Repo.update(changeset) do
      {:ok, _topic} ->
        conn
          |> put_flash(:info, "Topic updated")
          |> redirect(to: topic_path(conn, :index))
      {:error, changeset} ->
        render conn, "edit.html", changeset: changeset, topic: topic
    end

  end

  def delete(conn, %{"id" => topic_id}) do
    Repo.get!(Topic, topic_id)
    |> Repo.delete!

    conn
    |> put_flash(:info, "Topic deleted")
    |> redirect(to: topic_path(conn, :index))

  end

end
```

----

The line `use Discuss.Web, :controller` is used to imports the `controller` method from `web/web.ex` which defines all the behaviours that controller have.

Works is similar to class inheritance in OOP - extending the `BaseController` class.

----

The `conn` argument is a `Plug.Conn` struct, that represents both incoming request and outgoing response.

----

The `params` argument is a map that is used to parse the given URL. 

----

All methods must receive and return connection.

----

Functions with ! like `Repo.get!` on failure will abort to `404 error`.