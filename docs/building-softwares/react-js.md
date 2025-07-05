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

Just as the preceding example shows, any React component generally has two parts. In the first part, the component function performs some declarations (e.g. state variables, event handler functions, etc.), and in the last part, it returns a JSX.

Note importantly that _the function doesn't modify any variables (props, state variables, or ref variables) in its body_, it only declares the event handler functions that modify variables. Because a component function only _prepares_ the component, modification can _happen only after the component is rendered._

???+ question "Problem"
    Try modifying a prop or a state variable in the component function body, and see the error you get.

### Props

Parameterized components. Making components reusable.

Just as parameterized functions allow them to be used for different inputs, components with props also allow them to be used for different data.

Props are passed to components as attributes in JSX.

```javascript
import React from 'react';

function Greeting(props) { // can also use destructuring: ({ name })
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

## Hooks

### State variables

A component consists of a view and its logic. The view is rendered based on the data it has. When the data changes, the view should also change to reflect the new data.

Due to some user interactions (e.g. click), some data in a component may change. We may want the change to be reflected in the UI.

For example, a counter component that increments a number each time a button is clicked. Each time the button is clicked, the number should increase by one, and the UI should update to show the new number.

This cannot be achieved by ordinary variables, as they do not trigger re-renders when changed. React provides a way to manage such data using state variables.

Trigger re-renders when changed.

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

### Ref variables

Doesn't trigger re-renders when changed, but lives across re-renders. 

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

### Effects

Effects allow you to perform side effects in function components, such as data fetching, subscriptions, or manually changing the DOM. They run after the render phase.

```javascript
import React, { useEffect } from 'react';

function Timer() {
  useEffect(() => {
    const timer = setInterval(() => {
      console.log('Timer tick');
    }, 1000);

    return () => clearInterval(timer); // Cleanup on unmount
  }, []); // Empty dependency array means this effect runs once

  return <div>Timer is running</div>;
}
```

Effects, code that must execute after the component is rendered, are passed as a callback to the `useEffect` function.

Note that effects run _after the component is rendered._ For example, here's how an effect calling an API works: render the blank or placeholder JSX and update the state variables with values fetched from a server after that.

## Routing

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
