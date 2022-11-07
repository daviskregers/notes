# Adding relations

We will add an user_id to the `topics` table.

```elixir
def change do

    alter table(:topics) do
        add :user_id, references(:users)
    end

end
```

Then call `mix ecto.migrate` and modify the `web/models/topic.ex` model:

```elixir
schema "topics" do
    field :title, :string
    belongs_to :user, Discuss.User
end
```

As well as the user model:

```elixir
schema "users" do
    field :email, :string
    field :provider, :string
    field :token, :string

    has_many :topics, Discuss.Topic

    timestamps()
end
```

Now to test it

```elixir
iex(11)> Discuss.Repo.get(Discuss.Topic, 1)
[debug] QUERY OK source="topics" db=3.9ms queue=0.1ms
SELECT t0."id", t0."title", t0."user_id" FROM "topics" AS t0 WHERE (t0."id" = $1) [1]
%Discuss.Topic{
  __meta__: #Ecto.Schema.Metadata<:loaded, "topics">,
  id: 1,
  title: "New topic",
  user: #Ecto.Association.NotLoaded<association :user is not loaded>,
  user_id: nil
}
```

```elixir
iex(10)> Discuss.Repo.get(Discuss.User, 1)
[debug] QUERY OK source="users" db=1.6ms
SELECT u0."id", u0."email", u0."provider", u0."token", u0."inserted_at", u0."updated_at" FROM "users" AS u0 WHERE (u0."id" = $1) [1]
%Discuss.User{
  __meta__: #Ecto.Schema.Metadata<:loaded, "users">,
  id: 1,
  ...
  topics: #Ecto.Association.NotLoaded<association :topics is not loaded>,
}
```

Now we can modify the `TopicController` at the `create` method to include the user_id:

```elixir
# changeset = Topic.changeset(%Topic{}, topic)
changeset = conn.assigns.user
    |> build_assoc(:topics)
    |> Topic.changeset(topic)
```

We also might need to check whether the topic belogs to the user before editing, updating and deleting by using a function plug:

```elixir
plug :check_post_owner when action in [:update, :edit, :delete]

def check_topic_owner(conn, _params) do
    %{params: %{"id" => topic_id}} = conn

    if Repo.get(Topic, topic_id).user_id == conn.assigns.user.id do
        conn
    else
        conn
        |> put_flash(:error, "You cannot edit that")
        |> redirect(to: topic_path(conn, :index))
        |> halt()
    end
end
```

Also, edit the `web/templates/topic/index.html.eex`

```html
<%= if @conn.assigns.user.id == topic.user_id do %>
    <div class="right">
        <%= link "Edit", to: topic_path(@conn, :edit, topic) %>
        <%= link "Delete", to: topic_path(@conn, :delete, topic), method: :delete %>
    </div>
<% end %>
```

