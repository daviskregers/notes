# Learning cUrl

## Sources:
- https://www.tecmint.com/linux-curl-command-examples/
- https://www.baeldung.com/curl-rest

## API testing

### Verbose mode

When testing, it is a good idea to set verbose mode on:

```bash
curl -v http://deiveris.lv
```

```
curl -v http://deiveris.lv
* Rebuilt URL to: http://deiveris.lv/
*   Trying 146.185.159.146...
* TCP_NODELAY set
* Connected to deiveris.lv (146.185.159.146) port 80 (#0)
> GET / HTTP/1.1
> Host: deiveris.lv
> User-Agent: curl/7.58.0
> Accept: */*
> 
< HTTP/1.1 301 Moved Permanently
< Server: nginx/1.10.3 (Ubuntu)
< Date: Thu, 07 Mar 2019 09:33:02 GMT
< Content-Type: text/html
< Content-Length: 194
< Connection: keep-alive
< Location: https://deiveris.lv/
< 
<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx/1.10.3 (Ubuntu)</center>
</body>
</html>
* Connection #0 to host deiveris.lv left intact
```

By default it outputs the response body to `stdout`, we can also specify to save it as a file:

```bash
curl -o out.json http://domain.com/index.html
```

### HTTP Methods with cURL

#### GET

```bash
curl -v http://domain.com/path/to/something
```

#### POST

- The simple way of sending data:

```bash
curl -d 'id=9&name=deivs' http://domain.com:8080/path/to/something
```

- Passing a file that contains the request body:

```bash
curl -d @request.json -H "Content-Type: application/json" http://domain.com:8080/path/to/something
```

#### PUT 

This method is very similar to POST, but we use it when we want to send a new version of an existing resource.
To do this, we use the `-X` option.

```bash
curl -d @request.json -H 'Content-Type: application/json' -X PUT http://domain.com:8080/path/to/something
```

#### DELETE

We can specify to delete by using the `-X` option as well.

```bash
curl -X DELETE http://domain.com:8080/path/to/something/9
```

### Custom headers

We can replace the default headers or add our own

```bash
curl -H "Host: com.domain.com" http://domain.com
```

```bash
curl -H "User-Agent:" http://domain.com
```

### Authentication

For basic authentication we can use:

```bash
curl --user username:password http://domain.com
```

If we want to use `OAuth2`, we'll need to get the `access_token`:

```json
{
  "access_token": "b1094abc0-54a4-3eab-7213-877142c33fh3",
  "token_type": "bearer",
  "refresh_token": "253begef-868c-5d48-92e8-448c2ec4bd91",
  "expires_in": 31234
}
```

Now we can use:

```
curl -H "Authorization: Bearer b1094abc0-54a4-3eab-7213-877142c33fh3" http://domain.com
```

## Examples

### Viewing version

```bash
curl --version
```

### Download a file

You can use `-O` or `-o` flags.
The `-O` will save the file in the `CWD` with the same filename as on the remote.

```bash
curl -O http://domain.com/file.tar.gz # save as $CWD/file.tar.gz
```

The `-o` will require you specifying where to save the file:

```bash
curl -o /tmp/renamed.tar.gz http://domain.com/file.tar.gz # save to /tmp/renamed.tmp.gz
```

### Resume an interrupted download

If a download was interrupted for some reason, it can be resumed by using the `-C - ` flag.

```bash
curl -C - -O http://domain/file.tar.gz
```

### Download multiple files

You can chain multiple flags of the same type:

```bash
curl -O http://domain.com/index1.html -O http://domain.com/index2.html
```

### Download URLs from a file

You can combine `curl` with `xargs` to download files from a list of URLs in a file.

```txt
http://domain.com/index1.html
http://domain.com/index2.html
http://domain.com/index3.html
```

```bash
xargs -n 1 curl -O < listurls.txt
```

### Use a Proxy with or without Authentication

If you are behind a proxy server lisyening on port `8080` at `proxy.domain.com`:

```bash
curl -x proxy.domain.com:8080 -U user:password -O http://domain.com/file.tar.gz
```

### Query HTTP Headers

`HTTP` headers allow the remote web server to send additional information about itself along with the actual request. This provides the client with details on how the request is handled.

```bash
curl -I http://deiveris.lv
```

```
HTTP/1.1 301 Moved Permanently
Server: nginx/1.10.3 (Ubuntu)
Date: Thu, 07 Mar 2019 09:20:21 GMT
Content-Type: text/html
Content-Length: 194
Connection: keep-alive
Location: https://deiveris.lv/
```

### Make a POST request with parameters

You can send POST data with it as well:

```bash
curl --data "firstName=John&lastName=Doe" https://domain.info.php
```

### Download files from an FTP server with or without authentication

```bash
curl -u username:password -O ftp://domain.com/file.tar.gz
```

### Upload files to FTP server

```bash
curl -u username:password -Y local.tar.gz ftp://domain.com
```

### Specify User Agent

The `user agent` is part of the information that is sent along with an `HTTP` request. This indicates which browser the client used to make the request. 

```bash
curl -I http://deiveris.lv --user-agent "This is a CURL browser"
```

### Store website cookies

You can check what cookies are downloaded when visiting a site by using a command:

```bash
curl --cookie-jar saved.txt https://domain.com
```

### Send website cookies

You can use the stored cookies in the last section, to make subsequent requests:

```bash
curl --cookie saved.txt https://domain.com
```

### Modify Name Resolution

If you want to test a local version of `domain.com` before pushing it live, you can make a curl resolve:

```bash
curl --resolve www.domain.com:80:localhost http://www.domain.com
```

### Limit Download rate

You can limit your downloads. The following command will limit it to `100KB/s`.

```bash
curl --limit-rate 100K http://domain.com/file.tar.gz
```

