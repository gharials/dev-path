# Software Development Concepts

## API (Application Programming Interface)

Before understanding APIs in general, we need to understand what an interface is.

### What is an interface?

We have sockets for lights at every home. Providing power and making lights are two different areas. A light socket acts as a link or bridge between them. _These type of links or bridges are called interfaces._ Lights need power, but light manufacturers don't need to worry about it. They just need to make sure that there lights’ connectors are compatible with the socket design used at homes. As a result, light manufacturers can focus on making lights of many designs, shapes, sizes, and colors.

All complex systems are built using interfaces of some kind. _Interfaces allow two parties work independently._ Power manufacturers can improve cables, power supplies, etc., while light manufacturers can improve light technologies (e.g., CFL, LED, etc.). No parties create any problem for the other, because the interface remains the same.

### What is an API?

By default, a programming language has very few built-in features. Therefore, very few things can be done using just the language itself, like printing on the console. A real program needs to do many other things outside that.

For example, a JavaScript program may need to make HTTP requests from it. Making HTTP requests to a server and receiving responses is a very complex operation. Understanding and implementing it requires deep knowledge of HTTP, networking, and operating systems. Here, the `fetch` function acts as an interface between HTTP and a JavaScript program. Some programmer had the HTTP request-response mechanism implemented in the `fetch` function once, and any caller can use it to make HTTP requests.

This way, the `fetch` function enables other programmers to program new applications using HTTP. That's why it is called an _application programming interface_ (API). Like the `fetch` function hides the complexity of HTTP, many other APIs hide the complexity of other systems.

In an API, both parties agree on a set of rules. For example, in the `fetch` function, the caller has to know how to call it, what parameters to pass, and what it returns. The programmer of the `fetch` function makes sure that it follows the agreed rules. The caller doesn't need to know _how `fetch` is implemented internally_. The caller just needs to know _how to use it_.

So, whenever you want to use a complex system in your program, you can install a library that provides an API for that system. You can then use that API to communicate with the complex system without worrying about its internal details.
