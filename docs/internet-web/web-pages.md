# How Web Pages Work

A web page is primarily an HTML document. A server only [transfers the HTML document](./web-servers.md#how-an-http-server-serves-websites) and related files to the browser when a user requests a web page. The HTML document contains the content that the user sees on the web page.

## The fundamental building blocks of a web page

* _HTML document._ For displaying the content to the user.
* _Images._ For displaying images on the page.
* _CSS._ For styling the content.
* _JavaScript._ For making the web page interactive.

The HTML document is the main file of a web page. But a complex web page needs some additional files (images, CSS files, scripts, etc.), called *linked resources.*

!!!info
    **Passing CSS and JavaScript within HTML**

    CSS and JavaScript can also be passed within the HTML document itself, instead of linking them as external resources. This is done with the `<style>` and `<script>` tags, respectively. Example follows:

    ```html
    <html>
    <head>
      <style>
        body {
          background-color: lightblue;
        }
      </style>
      <script>
        function greet() {
          alert("Hello, World!");
        }
      </script>
    </head>
    <body onload="greet()">
      <h1>Welcome to My Web Page</h1>
      <p>This is a simple web page.</p>
    </body>
    </html>
    ```

## Linking resources with HTML

The resources needed by an HTML are specified with the `<link>` tag within the `<head>` tag of the HTML document. The external resources are usually stored in the server's [static directory](websites.md#serving-static-contents). After receiving an HTML, browsers [send requests to the server](./web-servers.md#how-an-http-server-serves-websites) for each of the specified resources.

An HTML may also need JavaScript files. They are specified as external resources with the `<script>` tag.

## Browser as a JavaScript runner

Like NodeJS (the `node` command), every browser can run JavaScript programs too. In fact, JavaScript was originally designed only to be run on browsers and remained so for a long time, NodeJS came later.
    
Where NodeJS can run *any* JavaScript file, browsers can *only* run JavaScript files included in HTML files. JavaScript running on a browser is called *client-side JavaScript*, and running on a server with NodeJS is called *server-side JavaScript.* As we will see, client-side JavaScript works together with the HTML document and helps in making web pages interactive.

Users can interact with client-side JavaScript from browser console.

### JavaScript DOM

Most importantly, client-side JavaScript has access to the HTML document's _object representation_, called [DOM](https://www.w3schools.com/js/js_htmldom.asp) (Document Object Model), through a special object named `document`. The object is created automatically and is accessible from everywhere in any client-side JavaScript file. Elements of the HTML document can be read and modified through the `document` object. This allows JavaScript to dynamically change the content, structure, and style of a webpage.

## How HTML and client-side JavaScript work together

HTML elements can associate functions with its _events_; those functions are called _event handlers._ For example, `<element onClick="function1()"/>` means call `function1` when element is clicked; `<element onLoad="function2()"/>` means call `function2` when element loads. Here both `function1` and `function2` are defined in the linked JavaScript files. Here is an exhaustive list of [HTML events](https://www.w3schools.com/jsref/dom_obj_event.asp).

An HTML file may have one or more associated JavaScript files containing the functions associated with various events in the HTML file. Functions have access to the HTML document with the `document` object. HTML elements can be accessed with the `document` object in [several ways](https://www.w3schools.com/js/js_htmldom_document.asp): `document.getElementById` is a popular way.

The architecture in summary: _perform some operation (function) when something happens (event) to an element._

## Applications of client-side JavaScript

### Validating forms with client-side JS

Client-side JavaScript has its application in *validating* HTML forms. Users may input incorrect data or forget to input mandatory data in forms. The user inputs have to be checked (called *validation*) before storing in database.

!!!info
    **How HTML forms work.**

    Forms are used to accept inputs from user and passing them to server for storing in database. A form contains a number of inputs of various types and a submit button. When user clicks the submit button, the inputs are passed (*submitted*) to the server.

    A server has a URL that handles the form data. The URL that handles the form data is specified in the `action` attribute (e.g., `<form action="/submit">`). The request method can also be specified with the `method` attribute (e.g., `<form action="/submit" method="POST">`. Method can be either `GET` or `POST`. Upon submitting the form, the form fields are converted into a request body and sent to the server at the specified URL. The server processes the request and returns a response.

In a simple HTML form, the data can be validated by the server only after the user submits the form. This approach unnecessarily wastes network travel cost and server resources.

If the form data could be validated at the browser, before submitting to server, both network travel and server processing could be avoided. Client-side JavaScript is very useful for this purpose: write a JavaScript function that contains the logic to validate the form. In the function, find the form element using the `document` object. Access and check the form input values. Call the function when user clicks the submit button. Submit to server only after the function finds no error in the inputs.
