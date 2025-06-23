# React JS

Generating HTML using JavaScript functions demo.

Components instead of a large single HTML file. JavaScript functions generating parts of the HTML document.

## Components

### JSX

React uses JSX, a syntax extension that allows writing HTML-like code within JavaScript. JSX makes it easier to visualize the UI structure and is transformed into JavaScript function calls.

JavaScript expression can be embedded in JSX using curly braces `{}`.

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

### Component functions

Functions returning JSX are called components.

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

## Routing

Some components are associated with specific URLs, allowing navigation between different views in a single-page application (SPA). React Router is a popular library for handling routing in React applications.

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