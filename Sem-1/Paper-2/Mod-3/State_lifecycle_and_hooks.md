# Understanding State, Lifecycle, and Hooks

## 1. Basic idea of component lifecycle

Every component goes through three phases:

1. **Mounting**: the component appears on the screen for the first time
2. **Updating**: it re-renders because its state or props changed
3. **Unmounting**: it is removed from the screen

In functional components, hooks (mainly `useEffect`) let you run code at these points.

## 2. Hooks

Hooks are special functions (they start with `use`) that let functional components use state and other React features.

**Rules of hooks:**
- Call them only at the top level of a component (not inside loops, conditions or nested functions)
- Call them only inside components or custom hooks

### useState

Stores a value that, when changed, makes the component re-render.

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>+</button>
      <button onClick={() => setCount(count - 1)}>-</button>
      <button onClick={() => setCount(0)}>Reset</button>
    </div>
  );
}
```

`count` is the current value, `setCount` is the function that updates it, and `0` is the starting value. Never change state directly (`count = 5`), always use the setter.

### useEffect

Runs code **after** the component renders. Used for side effects like fetching data, timers and subscriptions.

```jsx
import { useState, useEffect } from "react";

function Example() {
  const [data, setData] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(result => setData(result));
  }, []); // [] means: run only once, when the component mounts

  return <p>Users loaded: {data.length}</p>;
}
```

**The dependency array controls when it runs:**

| Code | Runs |
|---|---|
| `useEffect(() => {...})` | After every render |
| `useEffect(() => {...}, [])` | Only once, on mount |
| `useEffect(() => {...}, [count])` | On mount, and whenever `count` changes |

**Cleanup** (runs on unmount, or before the effect runs again):

```jsx
useEffect(() => {
  const timer = setInterval(() => console.log("tick"), 1000);
  return () => clearInterval(timer);
}, []);
```

### useRef

Holds a value that **persists between renders without causing a re-render**. Often used to access a DOM element directly.

```jsx
import { useRef } from "react";

function FocusInput() {
  const inputRef = useRef(null);

  return (
    <>
      <input ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus</button>
    </>
  );
}
```

**useState vs useRef:** changing state re-renders the component, changing `ref.current` does not.

## 3. How state changes affect the UI

1. User does something (like clicking)
2. A state setter is called
3. React re-renders that component with the new state
4. React updates only the changed parts of the real DOM

The UI is a result of the state: change the state, and the UI follows.

## 4. Side effects and rendering flow

A **side effect** is anything that reaches outside the component's own rendering, such as API calls, timers or changing the page title.

**Flow:**

```
Render (component function runs) -> Commit (DOM updated) -> useEffect runs
```

Effects never run during rendering itself, only after the screen has been updated. In development, React's Strict Mode may run effects twice on mount to help catch bugs. This does not happen in the production build.
