# S3 CORS Hands On

We can modify the previously uploaded index.html file:

```html
<html>
    <head>
        <title>My First Webpage</title>
    </head>
    <body>
        <h1>Hello World!</h1>

        <div id="tofetch" />

        <script>
            var tofetch = document.getElementById('tofetch');
            fetch('extra-page.html')
            .then((response) => response.text())
            .then((html) => tofetch.innerHTML = html)
        </script>
    </body>
</html>
```

And add an extra-page.html:

```html
<p>This <strong>extra page</strong> has been sucessfully loaded!</p>
```

If we view the index, we can see that it works:

![](2022-02-10-07-37-05.png)

This works because we have the same origin, but if we create a new bucket now and store the extra-page there:

```html
<html>
    <head>
        <title>My First Webpage</title>
    </head>
    <body>
        <h1>Hello World!</h1>

        <div id="tofetch" />

        <script>
            var tofetch = document.getElementById('tofetch');
            fetch('https://demo-dave-extra.s3.eu-west-1.amazonaws.com/extra-page.html')
            .then((response) => response.text())
            .then((html) => tofetch.innerHTML = html)
        </script>
    </body>
</html>
```

![](2022-02-10-07-42-27.png)

We can go to permissions and set the CORS settings for the second bucket:

```json
[
    {
        "AllowedHeaders": ["Authorization"],
        "AllowedMethods": ["GET"],
        "AllowedOrigins": [
            "http://demo-dave-s3-bucket.s3-website-eu-west-1.amazonaws.com"
        ],
        "ExposeHeaders": [],
        "MaxAgeSeconds": 3000
    }
]
```

![](2022-02-10-07-46-30.png)

And now it works:

![](2022-02-10-07-47-13.png)