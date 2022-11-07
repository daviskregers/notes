# Phoenix router

The router file is located at `web/router.ex`. It is used to route a specific incoming request URL to a specific controller.

The router file mostly consists of plug configuration and route configuration. 

The first thing is plugs. This defines what middleware / plugs are executed in what order through when a new request arrives.

```elixir
pipeline :browser do
    plug :accepts, ["html"]
    plug :fetch_session
    plug :fetch_flash
    plug :protect_from_forgery
    plug :put_secure_browser_headers
end

pipeline :api do
    plug :accepts, ["json"]
end
```

Then, you can define routes in a following manner:

```elixir
scope "/", Discuss do
    pipe_through :browser # Use the default browser stack

    get     "/",                TopicController, :index
    # get     "/topics/new",      TopicController, :new
    # post    "/topics",          TopicController, :create
    # get     "/topics/:id/edit", TopicController, :edit
    # put     "/topics/:id",      TopicController, :update
    # delete  "/topics/:id",      TopicController, :delete

    resources "/topics", TopicController
end
```

You can define the routes one by one, but if you follow the RESTful approach, you can define them as resources.