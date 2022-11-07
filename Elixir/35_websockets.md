# WebSockets in Phoenix

## Preparation

We will create comment section that will work in real time using websockets.

In order to do that, first we create comments:

```bash
mix ecto.gen.migration add_comments
```

```elixir
create table(:comments) do
    add :content, :string
    add :user_id, references(:users)  
    add :topic_id, references(:topics)
end
```

Make the comment model in `web/models/comment.ex`:

```elixir
defmodule Discuss.Comment do
  use Discuss.Web, :model

  schema "comments" do
    field :content, :string
    belongs_to :user, Discuss.User
    belongs_to :topic, Discuss.Topic
  end

  def changeset(struct, params \\ %{}) do
    struct
    |> cast(params, [:content, :user_id, :topic_id])
    |> validate_required([:content, :user_id, :topic_id])
  end

end
```

And modify the `User` and `Topic` models.

```elixir
has_many :comments, Discuss.Comment
```

## Actual WebSockets

Phoenix has built in WebSockets support to exchange information in real-time. It also supports alternatives like HTTP Long Polling.

WebSockets have implementation both on server-side and client-side.

On the server side, the web socket configuration can be managed in the `web/channels` directory.

The client side can be managed using the `web/static/js/socket.js` file.

The WebSockets interface is split into a separate channels which is similar to a controller. It has multiple methods like `join`, `handle_in`.

So, we can start with creating a connection on the client side by modifying the `web/static/js/socket.js`

```javascript

import {Socket} from "phoenix"
let socket = new Socket("/socket", {params: {token: window.userToken}})
socket.connect()

const createSocket = (topicId) => {

  let channel = socket.channel('comments:' + topicId, {})
  channel.join()
    .receive("ok", resp => { renderComments(resp.comments) })
    .receive("error", resp => { console.log("Unable to join", resp) })
  
  document.querySelector('button').addEventListener('click', function(e) {
    e.preventDefault()
    const textarea = document.querySelector('textarea')
    const content = textarea.value
    channel.push('comments:add', {content: content})
    textarea.value = "";
  })

  channel.on(`comments:${topicId}:new`, renderComment)
  
}

function renderComments(comments) {
  console.log('connected', comments)
  const renderedComments = comments.map(commentTemplate)
  document.querySelector('.collection').innerHTML = renderedComments.join('')
}

function renderComment(event) {
  const renderedComment = commentTemplate(event.comment);
  document.querySelector('.collection').innerHTML += renderedComment;
}

function commentTemplate(comment) {

  const author = (comment.user == null) ? "Anonymous" : comment.user.email;

  return `
      <li class="collection-item">
        ${comment.content}
        <div class="right">
          ${author}
        </div>
      </li>
    `;
}

window.createSocket = createSocket

```

Then we import this file in `web/static/js/app.js`

```javascript
import "./socket"
```

After that, we modify the `web/templates/topic/show.html.eex` template:

```html
<h5><%= @topic.title %></h5>

<ul class="collection">
</ul>

<div class="input-field">
    <textarea class="materialize-textarea"></textarea>
    <button class="btn">Add comment</button>
</div>

<script>
document.addEventListener("DOMContentLoaded", function() {
    window.createSocket(<%= @topic.id %>)
})
</script>
```

Add the `comments` channel to the `web/channels/user_socket.ex` which is a `routes.ex`-like file for WebSockets.

```elixir
defmodule Discuss.UserSocket do
  use Phoenix.Socket

  channel "comments:*", Discuss.CommentsChannel

  transport :websocket, Phoenix.Transports.WebSocket

  def connect(%{"token" => token}, socket) do
    case Phoenix.Token.verify(socket, "key", token) do
      {:ok, user_id} ->
        {:ok, assign(socket, :user_id, user_id)}
      {:error, _reason} ->
        {:ok, assign(socket, :user_id, nil)}
    end
  end

  def id(_socket), do: nil

end
```

Notice, that it handles authentication too, it is handled by using a token that is set in `web/templates/layout/app.html.eex`

```html
<%= if @conn.assigns.user do %>
<script>
    window.userToken = "<%= Phoenix.Token.sign(Discuss.Endpoint, "key", @conn.assigns.user.id) %>";
</script>
<% end %>
```

Then finally, we add the `web/channels/comments_channel.ex`

```elixir
defmodule Discuss.CommentsChannel do

  use Discuss.Web, :channel
  alias Discuss.Topic
  alias Discuss.Comment
  alias Discuss.User

  def join("comments:" <> topic_id, _params, socket) do

    topic_id = String.to_integer(topic_id)

    topic = Topic
    |> Repo.get(topic_id)
    |> Repo.preload(comments: [:user])

    {:ok, %{comments: topic.comments}, assign(socket, :topic, topic)}

  end

  def handle_in("comments:add", %{"content" => content}, socket) do

      topic = socket.assigns.topic
      user_id = socket.assigns.user_id

      changeset = topic
      |> build_assoc(:comments, user_id: user_id)
      |> Repo.preload(:user)
      |> Comment.changeset(%{content: content, user_id: user_id})

      case Repo.insert(changeset) do
        {:ok, comment} ->
          broadcast!(socket, "comments:#{socket.assigns.topic.id}:new", %{comment: comment})
          {:reply, :ok, socket}
        {:error, _reason} ->
          {:reply, {:error, %{errors: changeset}}, socket}
      end

  end

end
```

The last things to do, since the the websockets uses JSON encode, we need to modify the `Comment` and `User` model in order to tell them on how to encode them:

```elixir
defmodule Discuss.Comment do
  use Discuss.Web, :model

  @derive {Poison.Encoder, only: [:content, :user]}

  schema "comments" do
    field :content, :string
    belongs_to :user, Discuss.User
    belongs_to :topic, Discuss.Topic
  end

  def changeset(struct, params \\ %{}) do
    struct
    |> cast(params, [:content])
    |> validate_required([:content])
  end

end
```

```elixir
defmodule Discuss.User do
  use Discuss.Web, :model

  @derive {Poison.Encoder, only: [:email]}

  schema "users" do
    field :email, :string
    field :provider, :string
    field :token, :string

    has_many :topics, Discuss.Topic
    has_many :comments, Discuss.Comment

    timestamps()
  end

  @doc """
  Builds a changeset based on the `struct` and `params`.
  """
  def changeset(struct, params \\ %{}) do
    struct
    |> cast(params, [:email, :provider, :token])
    |> validate_required([:email, :provider, :token])
  end
end
```