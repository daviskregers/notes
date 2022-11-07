# Phoenix Model Layer

The model layer is mostly used to get data from the database and interact with it.

## Migration files

We can create migration files to tell phoenix to change the database. We can use a command to generate it:

```bash
mix ecto.gen.migration add_topics
```

The migration file will be stored in `priv/repo/migrations` directory.

The migration file will contain a set of instructions for phoenix on how to change the database.

So, if we want to create a table `topics` with a column `title` of type `string` we can use the following code:

```elixir
defmodule Discuss.Repo.Migrations.AddTopics do
  use Ecto.Migration

  def change do

    create table(:topics) do
      add :title, :string
    end

  end
end
```

Example on alter / reference

```elixir
def change do

    alter table(:topics) do
        add :user_id, references(:users)
    end

end
```

The migration process can be executed by running a command:

```bash
mix ecto.migrate
```

## Model files

The models are located into `web/models` directory. 

We can create a new `Topic` model by creating a `web/models/topic.ex` file with following content.

```elixir
defmodule Discuss.Topic do
  use Discuss.Web, :model

  schema "topics" do
    field :title, :string
  end

  def changeset(struct, params \\ %{}) do
    struct
    |> cast(params, [:title])
    |> validate_required([:title])
  end

end
```

----

The line `use Discuss.Web, :model` is used to imports the `model` method from `web/web.ex` which defines all the behaviours that controller have.

Works is similar to class inheritance in OOP - extending the `BaseModel` class.

----

The schema part describes which table and columns to use.

----

The changeset function computes a changed model. It accepts the struct (current model) and the hash with all the properties to update.

- It casts it - produces the changeset,
- validates it - adds errors to the changeset if there are any
- Returns the changeset

We can produce the changeset by doing following

```elixir
iex(3)> struct = %Discuss.Topic{}
%Discuss.Topic{
  __meta__: #Ecto.Schema.Metadata<:built, "topics">,
  id: nil,
  title: nil
}
iex(4)> params = %{title: "A new Topic"}
%{title: "A new Topic"}
iex(5)> Discuss.Topic.changeset(struct, params)
#Ecto.Changeset<
  action: nil,
  changes: %{title: "A new Topic"},
  errors: [],
  data: #Discuss.Topic<>,
  valid?: true
>
```

----

