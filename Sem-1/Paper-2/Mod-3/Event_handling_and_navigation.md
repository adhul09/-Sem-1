# Understanding Event Handling and Navigation

## 1. Event handling

React events are written in camelCase and take a **function**, not a string.

### onClick

```jsx
function Button() {
  const handleClick = () => {
    alert("Clicked!");
  };

  return <button onClick={handleClick}>Click me</button>;
}
```

**Common mistake:** `onClick={handleClick()}` calls the function immediately on render. Pass the function itself (`onClick={handleClick}`), or wrap it (`onClick={() => handleClick(5)}`) when you need to pass an argument.

### onChange

Fires whenever an input's value changes. Combined with state, it makes a **controlled input**.

```jsx
import { useState } from "react";

function NameInput() {
  const [name, setName] = useState("");

  return (
    <div>
      <input
        type="text"
        value={name}
        onChange={(e) => setName(e.target.value)}
      />
      <p>You typed: {name}</p>
    </div>
  );
}
```

`e.target.value` is the current text in the input.

## 2. Routing using React Router

React Router lets a single-page app show different "pages" without reloading the browser.

**Install:**

```bash
npm install react-router-dom
```

**Set up in main.jsx:**

```jsx
import { BrowserRouter } from "react-router-dom";

createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

**Define routes in App.jsx:**

```jsx
import { Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import About from "./pages/About";

function App() {
  return (
    <>
      <nav>
        <Link to="/">Home</Link>
        <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </>
  );
}
```

- `Routes` / `Route`: match a URL path to a component
- `Link`: works like `<a>` but does **not** reload the page

## 3. Navigation

### useNavigate

Lets you change pages from code, for example after a form submit or login.

```jsx
import { useNavigate } from "react-router-dom";

function Login() {
  const navigate = useNavigate();

  const handleLogin = () => {
    // ...login logic
    navigate("/dashboard");
  };

  return <button onClick={handleLogin}>Login</button>;
}
```

### Difference from older useHistory

| | useHistory (React Router v5) | useNavigate (v6 and later) |
|---|---|---|
| Go to a page | `history.push("/home")` | `navigate("/home")` |
| Replace current page | `history.replace("/home")` | `navigate("/home", { replace: true })` |
| Go back | `history.goBack()` | `navigate(-1)` |

`useHistory` was removed in v6. `useNavigate` is simpler: it returns a single function instead of a history object.
