# Forms in Phoenix

In order to get started with forms, we create a new view in `web/views/topic_view.ex` with the following content:

```elixir
defmodule Discuss.TopicView do
  use Discuss.Web, :view
end
```

And create templates in `web/templates/topic/new.html.eex` so it matches with the `TopicController` method `new`.

```html
<%= form_for @changeset, topic_path(@conn, :create), fn f -> %>
    <div class="form-group">
        <%= text_input f, :title, placeholder: "Title", class: "form-control" %>
        <%= error_tag f, :title %>
    </div>
    <%= submit "Save Topic", class: "btn btn-primary" %>
<% end %>
```

We can create `web/templates/topic/index.html.eex` with following:

```html
<h2>Topics</h2>

<ul class="collection">
    <%= for topic <- @topics do %>
        <li class="collection-item">
            <%= link topic.title, to: topic_path(@conn, :show, topic) %>
            <div class="right">
                <%= link "Edit", to: topic_path(@conn, :edit, topic) %>
                <%= link "Delete", to: topic_path(@conn, :delete, topic), method: :delete %>
            </div>
        </li>
    <% end %>
</ul>

<div class="fixed-action-btn">
    <%= link to: topic_path(@conn, :new), class: "btn-floating btn-large waves-effect waves-light red" do %>
        <i class="material-icons">add</i>
    <% end %>
</div>
```

Create `web/templates/topic/edit.html.eex`

```html
<%= form_for @changeset, topic_path(@conn, :update, @topic), fn f -> %>

    <div class="form-group">
        <%= text_input f, :title, placeholder: "Title", class: "form-control" %>
        <%= error_tag f, :title %>
    </div>

    <%= submit "Save Topic", class: "btn btn-primary" %>

<% end %>
```