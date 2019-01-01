# View vs template

In phoenix there are two folders in the `web` directory - `web/views` and `web/templates`, where the `web/views` is the MVC component.

When phoenix first boots up, it looks at the `web/views` folder and looks up every module in it.

It takes names of the view (`Discuss.PageView` module's name will be `Page`), then it will look at the templates directory for a folder that matches the name, in this example - the `page` folder.

Because these folders match, we can call
`PageView.render("index.html")` which will return the `web/templates/page/index.html` template.