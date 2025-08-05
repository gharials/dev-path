# Building web applications with React JS

!!! info "Prerequisite"
    Have a look at the [How Web Pages Work](../internet-web/web-pages.md) article as a prerequisite to this article.

In traditional web development, for each web page, developers create a single large HTML file and links CSS and JavaScript to it. In this approach, it becomes harder to add new features and to fix bugs as the application becomes larger.

React framework promotes a _modular development_ approach, meaning developing a web page in small components instead of a large single HTML file. Each component contains a part of the web page. React merges the components into a single HTML file before sending it to the user.

## React components

Component is the most important React concept. A component is a JavaScript function that creates a part of a web page whenever it is called. Here follows how a basic React component function looks like:

```javascript
import React from 'react';

function App() {
  return (
    <div>
      <h1>Hello, World!</h1>
      <p>This is a simple React component.</p>
    </div>
  );
}

export default App;
```

A component function returns JSX instead of HTML. JSX is an extension of HTML, which allows using JavaScript expression within HTML.

## How React generates web pages with components

In a React project, we only define the component functions, but how does React generate HTML from them? It is documented in [official React docs](https://react.dev/learn/render-and-commit). Here follows a brief overview of how a web page is created by React from component:

1. When a user requests for a web page, React finds out the respective component. This phase is called _trigger._
2. After a trigger, React generates the HTML string by calling the component function. This phase is called _rendering._
3. Then it adds the generated HTML portion into the HTML DOM using [`appendChild`](https://www.w3schools.com/jsref/met_document_createelement.asp) so that it becomes visible in the HTML page. This phase is called _commit._ .

While rendering a component, if React finds out that it contains child components, it triggers their rendering too. Those components also go through the _trigger_, _render_, and _commit_ phases.

## Working with React components

### General structure of a component

```javascript hl_lines="4-8 10-15"
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);
  
  let increment= () => {
    setCount(count + 1)
  }
  
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={increment()}>Click me</button>
    </div>
  );
}
```

Just as the preceding example shows, any React component generally has two parts. In the first part, the component function performs some declarations (e.g. state variables, event handler functions, etc.), and in the last part, it returns a JSX. Depending on situation, a component may have more variables and event handlers, and the JSX may be larger, but the general structure remains the same.

Note importantly that _the function doesn't modify any variables (props, state variables, or ref variables) in its body_, it only declares the event handler functions that modify variables. Because a component function only _prepares_ the component, modification can _happen only after the component is rendered._

???+ question "Problem"
    Try modifying a prop or a state variable in the component function body, and see the error you get.

### Reusing components with props

We have already learned, React component functions produce parts of a web page. In many web pages, we often see _repeated parts with different data._ For example, a bus ticket booking website may display a list of available buses in a list of cards. Each card is same in structure but contain different data for different buses.

For such scenarios, React uses parameterized components, making components _reusable_. Parametrized components define a parameter called `props` (short for properties). Properties of the `props` variable are the data passed by the valler. Just as parameterized functions can be used for different inputs, components with props also can be used for different data.

As the following example shows, props are passed to components as attributes in JSX.

```javascript
import React from 'react';

function Greeting(props) { // can be simplified with destructuring: ({ name })
  return <h1>Hello, {props.name}!</h1>;
}

function App() {
  return (
    <div>
      <Greeting name="Alice" />
      <Greeting name="Bob" />
    </div>
  );
}

export default App;
```

### Managing data in components

A component contains data too. A component broadly contains two kinds of data: first, data that require re-rendering when changed, and second, data that don't require a re-render when they are changed.

#### State variables

Some components start by displaying some initial value as data, and after that user interactions (e.g., clicks) may change the data. We want the updated value to be displayed in the UI. For example, a counter component displays 0 as its initial count, and each time a button is clicked, the count increments by 1. After each click, the component should show the updated count. Displaying the updated count requires _re-rendering_ the component.

This cannot be achieved with ordinary JavaScript variables, because they do not trigger re-renders when their values change. In React, such data must be declared as _state variables._ State variables mean variables that trigger a re-render of the component when their values change.

In the following example, `count` is declared as a state variable. A state variable is declared by calling the `useState` hook function. The function takes the initial value of the variable as a parameter and returns a variable and a function for updating the variable.

```javascript
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

#### Ref variables

A component may also contain data that are not displayed. Their values may change with events, but the updated values don't need to be displayed. In other words, they _do not trigger re-renders when their values change_. Moreover, we want those _data to be preserved after any re-render._

Ordinary JavaScript variables are not suitable for this purpose either, because they are lost after a re-render.

```javascript
import React, { useRef } from 'react';

function Timer() {
  const countRef = useRef(0);

  const handleClick = () => {
    countRef.current += 1;
    console.log(`Button clicked ${countRef.current} times`);
  };

  return (
    <div>
      <button onClick={handleClick}>
        Click me
      </button>
    </div>
  );
}
```

???+ question "Exercise"
    Try using an ordinary JavaScript variable instead of a Ref for the same purpose and see what happens.

### Effects: post-rendering operations in components

Just as an event handler function runs after a user event (e.g., a click), React provides a way to run a function _after a component is rendered._ This is called an _effect_. _An effect is a function that runs after the component is rendered and committed._

In React components, effects are passed as a callback to `useEffect` function. React will execute the callback _after rendering and committing the component._ Notice that an event handler function is run only when the event occurs, and it may never run if the event does not occur. But an effect function always runs after the component is rendered, regardless of any user event.

```javascript hl_lines="7-9"
import React, { useState, useEffect } from 'react';

function StudentDetails({ id }) {
  const [name, setName] = useState("");
  const [roll, setRoll] = useState("");

  useEffect(() => {
    // define the operations to be performed after rendering
  }, []);

  return (
    <div>
      <p>Name: {name}</p>
      <p>Roll: {roll}</p>
    </div>
  );
}
```

## Routing: navigating among components

A large web application consists of many web pages. Some process requires moving between multiple pages.

Some components are associated with specific URLs, allowing navigation between different views in a single-page application (SPA). React Router is a popular library for handling routing in React applications.

Registering a component in a router means this component will be available in this URL.

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Switch } from 'react-router-dom';

function Home() {
  return <h2>Home</h2>;
}

function About() {
  return <h2>About</h2>;
}

function App() {
  return (
    <Router>
      <Switch>
        <Route path="/about" component={About} />
        <Route path="/" component={Home} />
      </Switch>
    </Router>
  );
}
export default App;
```

## Client-side Rendering (CSR) and Server-side Rendering (SSR)

Generating HTML using JavaScript functions demo.

## React workflow

Divide planned web pages into components and develop the components first. Then compose the components together.
