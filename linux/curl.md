# Learning cUrl

## Viewing version

```bash
curl --version
```

## Download a file

You can use `-O` or `-o` flags.
The `-O` will save the file in the `CWD` with the same filename as on the remote.

```bash
curl -O http://domain.com/file.tar.gz # save as $CWD/file.tar.gz
```

The `-o` will require you specifying where to save the file:

```bash
curl -o /tmp/renamed.tar.gz http://domain.com/file.tar.gz # save to /tmp/renamed.tmp.gz
```

## Resume an interrupted download

If a download was interrupted for some reason, it can be resumed by using the `-C - ` flag.

```bash
curl -C - -O http://domain/file.tar.gz
```

## Download multiple files

You can chain multiple flags of the same type:

```bash
curl -O http://domain.com/index1.html -O http://domain.com/index2.html
```

## Download URLs from a file

You can combine `curl` with `xargs` to download files from a list of URLs in a file.

```txt
http://domain.com/index1.html
http://domain.com/index2.html
http://domain.com/index3.html
```

```bash
xargs -n 1 curl -O < listurls.txt
```

## Use a Proxy with or without Authentication

If you are behind a proxy server lisyening on port `8080` at `proxy.domain.com`:

```bash
curl -x proxy.domain.com:8080 -U user:password -O http://domain.com/file.tar.gz
```

## Query HTTP Headers

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

## Make a POST request with parameters

You can send POST data with it as well:

```bash
curl --data "firstName=John&lastName=Doe" https://domain.info.php
```

## Download files from an FTP server with or without authentication

```bash
curl -u username:password -O ftp://domain.com/file.tar.gz
```

## Upload files to FTP server

```bash
curl -u username:password -Y local.tar.gz ftp://domain.com
```

## Specify User Agent

The `user agent` is part of the information that is sent along with an `HTTP` request. This indicates which browser the client used to make the request. 

```bash
curl -I http://deiveris.lv --user-agent "This is a CURL browser"
```

## Store website cookies

You can check what cookies are downloaded when visiting a site by using a command:

```bash
curl --cookie-jar saved.txt https://domain.com
```

## Send website cookies

You can use the stored cookies in the last section, to make subsequent requests:

```bash
curl --cookie saved.txt https://domain.com
```

## Modify Name Resolution

If you want to test a local version of `domain.com` before pushing it live, you can make a curl resolve:

```bash
curl --resolve www.domain.com:80:localhost http://www.domain.com
```

## Limit Download rate

You can limit your downloads. The following command will limit it to `100KB/s`.

```bash
curl --limit-rate 100K http://domain.com/file.tar.gz
```

