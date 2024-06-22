# Useful React Functions and Hooks

React provides a variety of built-in functions and hooks that are essential for developing dynamic and interactive web applications. Here are some of the most commonly used and useful ones:

## useState

The `useState` hook is used to manage state in functional components.

```javascript {.line-numbers}
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>Click me</button>
    </div>
  );
}
```
