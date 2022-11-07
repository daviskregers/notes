# Server side templating

Server side templating is used when you want a collection of different web pages with distinct URLs that user can visit. It will serve a brand new HTML document.

The templates are located into `web/templates` directory. There will be two folders called `page` and `layout`. The files will have extension of `.eex`.

The `pages` folder is responsible for rendering separate pages, the `templates` folder is used to reuse different page layouts that the `pages` use.

By default, phoenix installs bootstrap css framework.