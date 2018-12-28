# Phoenix's MVC model

The MVC paradigm is split into 3 components:
- Model - processes the raw data
- View - a template that takes the model to look nice
- Controller - Figures out what the user is looking for, grabs the correct model, stuffs it into the view and returns to the user.

The phoenix framework uses this MVC paradigm in its workflow. All 3 of these components in the MVC model is located in the `web` directory - `web/controllers`, `web/models`, `web/views`.

So, in phoenix an incoming request works as follows:

- A request comes in
- It is processed by a router (`web/router.ex`), which routes it to a correct controller
- The controller takes a model, gets the data necessary and returns a view
- The view will get a template and compile the HTML of the response
- The response is sent to the user
