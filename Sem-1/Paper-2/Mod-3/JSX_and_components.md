# Understanding JSX and Component-Based Architecture

## 1. Difference between JSX and HTML

**JSX** looks like HTML but is actually JavaScript syntax. Vite/Babel converts it into normal JavaScript before the browser runs it.

| HTML | JSX |
|---|---|
| `class="box"` | `className="box"` |
| `for="name"` | `htmlFor="name"` |
| `onclick="fn()"` | `onClick={fn}` |
| `<img src="a.png">` | `<img src="a.png" />` (every tag must be closed) |
| `style="color: red"` | `style={{ color: "red" }}` (an object) |
| Multiple top-level elements allowed | Must return **one** parent (or a fragment `<> </>`) |

JSX also lets you put JavaScript inside `{ }`:

```jsx
const name = "Adhul";
const element = <h1>Hello, {name}! 2 + 2 = {2 + 2}</h1>;
```

## 2. What components are and why they are used

A **component** is a reusable piece of UI, like a button, a card or a navbar. A full page is built by combining many small components.

**Why use them:**
- Reusability: write once, use many times
- Easier to read and maintain
- Each part manages its own logic and look

## 3. Functional vs Class components

**Functional component** (modern, the standard way):

```jsx
function Welcome({ name }) {
  return <h1>Hello, {name}</h1>;
}
```

**Class component** (older style, basic idea only):

```jsx
import { Component } from "react";

class Welcome extends Component {
  render() {
    return <h1>Hello, {this.props.name}</h1>;
  }
}
```

Functional components with hooks are used in almost all new code. Class components still exist in older projects.

## 4. Concept of reusability

Props let the same component show different data:

```jsx
function Card({ title, price }) {
  return (
    <div className="card">
      <h3>{title}</h3>
      <p>Rs. {price}</p>
    </div>
  );
}

function App() {
  return (
    <>
      <Card title="Pen" price={10} />
      <Card title="Book" price={150} />
    </>
  );
}
```

One `Card` component, two different cards.

## 5. Dynamic rendering using data

Use `map` to render a list from an array. Each item needs a unique `key`.

```jsx
const products = [
  { id: 1, title: "Pen", price: 10 },
  { id: 2, title: "Book", price: 150 },
];

function App() {
  return (
    <div>
      {products.map(p => (
        <Card key={p.id} title={p.title} price={p.price} />
      ))}
    </div>
  );
}
```

**Conditional rendering:**

```jsx
{isLoggedIn ? <p>Welcome back</p> : <p>Please log in</p>}
```
