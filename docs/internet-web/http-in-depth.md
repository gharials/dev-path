# HTTP in depth

There are two basic components in the HTTP protocol: a server and some clients. Clients send requests to a server and the server returns responses. See this [resource](https://developer.mozilla.org/en-US/docs/Web/HTTP/Overview#http_flow) for understanding the request-response flow in detail.

## Fundamental HTTP concepts

The following subsections cover the concepts necessary to get started working with HTTP.

### URLs

URLs are used to identify a web server and access its _resources_. Here is how a URL look like:

`http://www.example.com(1):80(2)/path/to/myfile.html?(3)key1=value1&key2=value2#(4)SomewhereInTheDocument`
{ .annotate }

1. Host name: `www.example.com` (can be an IP address too).
2. Port number: `:80` (optional; assumed to be `80` unless specified otherwise).
3. Query parameter start indicator: `?` (optional; indicates that there are a few query parameters following it in key value format and separated by `&`).
4. Fragment indicator:  `#` (optional; text following it specifies the section in a web page).

URLs cannot contain any spaces. See this [resource](https://developer.mozilla.org/en-US/docs/Web/URI#urls) for further details.

### Requests and responses

Generally, HTTP requests and responses consists of some headers followed by a body. Request and response bodies maybe empty depending on requests or responses.

Here follows a representative example of an HTTP request:

```
GET / HTTP/1.1
Host: developer.mozilla.org
Accept-Language: fr
```

Here follows a representative example of an HTTP response:

```
HTTP/1.1 200 OK
Date: Sat, 09 Oct 2010 14:28:02 GMT
Server: Apache
Last-Modified: Tue, 01 Dec 2009 20:18:22 GMT
ETag: "51142bc1-7449-479b075b2891b"
Accept-Ranges: bytes
Content-Length: 29769
Content-Type: text/html

<!doctype html>… (here come the 29769 bytes of the requested web page)
```

### Request methods

Each HTTP request follows a _method_. Notice in the sample request that the first line contains the request method (`GET` in that case). The most commonly used request methods are the following: `GET`, `POST`, `PUT`, and `DELETE`.

!!! info
    Requests made from the browser address bars are always `GET` requests. Tools like curl or Postman lets you choose the request method.

### Status codes

Each HTTP response contains a status code, indicating the status of the operation---whether the operation succeeded, failed, or anything else. Notice in the sample response that the first line contains the status code (`200` in that case). Commonly used status codes are `200`, `201`, `404`, etc.

### Headers

HTTP requests and responses contain a number of _headers._ They follow this general key-value format: `Header-name: value`. Headers may vary per request and response. They serve as metadata or directives (instructions) either for the client or the server. For example, the `Content-Type` header in HTTP responses tells the client how to treat the response body.

!!! info
    An HTTP response sent by a server may contain any kind of data. Then how does a browser understand its format? The `content-type: text/html` header tells browsers that the content is an HTML page and browsers render it.

### Cookies

A special HTTP header called cookie (`Set-Cookie: <cookie-name>=<cookie-value>`) allow a server to pass some data to the client. The client is supposed to store this value and include it automatically in all subsequent requests as the `Cookie` header (e.g. `Cookie: <cookie-name>=<cookie-value>`).

A server forgets about requests and the hosts they came from after returning a response (that is why HTTP protocol is called _stateless_). A server can never tell from a series of requests it received whether they came from (originate) the same client or not. By sending random numbers as a cookie value and keeping track of the the cookie, a server can detect whether a request came from a known host or a new one.

Cookies have other useful applications too.