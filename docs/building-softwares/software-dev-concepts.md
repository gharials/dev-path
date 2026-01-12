# Software Development Concepts

## API (Application Programming Interface)

Before understanding APIs in general, we need to understand what an interface is.

### What is an interface?

We have sockets for lights at every home. Providing power and making lights are two different areas. A light socket acts as a link or bridge between them. _These type of links or bridges are called interfaces._ Lights need power, but light manufacturers don't need to worry about it. They just need to make sure that there lights’ connectors are compatible with the socket design used at homes. As a result, light manufacturers can focus on making lights of many designs, shapes, sizes, and colors.

All complex systems are built using interfaces of some kind. _Interfaces allow two parties work independently._ Power manufacturers can improve cables, power supplies, etc., while light manufacturers can improve light technologies (e.g., CFL, LED, etc.). No parties create any problem for the other, because the interface remains the same.

### What is an API?

A program may need to interact with many external systems. Writing code for every interaction with a system from scratch would be very complex and time-consuming. An API has it written once and lets other programmers use it whenever needed. These interfaces let you write other programs or applications using them. That is why they are called _application programming_ interfaces.
    
For example, a JavaScript program may need to make HTTP requests from it. Making HTTP requests to a server and receiving responses is a very complex operation. Understanding and implementing it requires deep knowledge of HTTP, networking, and operating systems. Here, the `fetch` function acts as an interface between HTTP and a JavaScript program. Someone had the HTTP request-response mechanism implemented in the `fetch` function once, and any caller can use it to make HTTP requests.
    
In an API, both parties agree on a set of rules. Firstly, the API represents or models a system. The caller (user of the API) has to know the model. Secondly, the caller has to know the rules of communication with the system. The caller then uses the API to communicate with the system.
