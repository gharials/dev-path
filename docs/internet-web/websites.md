# How websites work

## How an HTTP server serves websites

HTTP responses may contain many types of contents in their bodies and the content's type is indicated by the `Content-Type` header. Websites are nothing but a particular type of HTTP response that contains an HTML document in its body and its `Content-Type` header is set to `text/html`. A browser knows how to render an HTML page. An HTML page may refer to some other resources in it, like images, fonts, stylesheets, scripts, etc. Browsers download all resources associated with a page by separate automatic subsequent requests.

The following diagram shows how an HTML page (`/page.html`) is served by a server.

```mermaid
---
title: An HTTP server serving a sample HTML page
---
sequenceDiagram
    Client->>Server: /page.html
    Server-->>Client: page.html,content-type:text/html
    Client->>Server: image.jpg
    Server-->>Client: image.jpg,content-type:image/jpeg
    Client->>Server: style.css
    Server-->>Client: style.css,content-type:text/css
    Client->>Server: script.js
    Server-->>Client: script.js,content-type:text/javascript
```

The client (browser) sends a request for the `/page.html` page to the server; the server returns the page in response. The browser finds that the the HTML file refers to some other resources too, like an image (`image.jpg`), a stylesheet file (`style.css`), a script (`script.js`), etc. The browser makes requests for each of them to the server and the server returns them in response.
