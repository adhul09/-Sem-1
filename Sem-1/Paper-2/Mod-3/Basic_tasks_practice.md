# Apply Concepts 

## 1. Build small UI components

A small, reusable component that takes data through props.

```jsx
// components/ProfileCard.jsx
function ProfileCard({ name, role }) {
  return (
    <div className="profile-card">
      <h3>{name}</h3>
      <p>{role}</p>
    </div>
  );
}

export default ProfileCard;
```

```jsx
// Usage
<ProfileCard name="Adhul" role="Student" />
<ProfileCard name="Riya" role="Designer" />
```

## 2. Render dynamic lists using map

```jsx
const skills = ["HTML", "CSS", "JavaScript", "React"];

function SkillList() {
  return (
    <ul>
      {skills.map((skill, index) => (
        <li key={index}>{skill}</li>
      ))}
    </ul>
  );
}
```

Use a unique `id` as the `key` when your data has one. The index is fine only for simple, unchanging lists.

## 3. Handle user inputs and events

A simple to-do list: type a task, add it, remove it.

```jsx
import { useState } from "react";

function TodoApp() {
  const [task, setTask] = useState("");
  const [tasks, setTasks] = useState([]);

  const addTask = () => {
    if (task.trim() === "") return;
    setTasks([...tasks, task]);
    setTask("");
  };

  const removeTask = (indexToRemove) => {
    setTasks(tasks.filter((_, i) => i !== indexToRemove));
  };

  return (
    <div>
      <input
        value={task}
        onChange={(e) => setTask(e.target.value)}
        placeholder="Enter a task"
      />
      <button onClick={addTask}>Add</button>

      <ul>
        {tasks.map((t, i) => (
          <li key={i}>
            {t} <button onClick={() => removeTask(i)}>X</button>
          </li>
        ))}
      </ul>
    </div>
  );
}
```

**Concepts used:** `useState`, controlled input (`onChange`), `onClick`, spread operator (`[...tasks, task]`), `map` and `filter`.

## 4. Create a multi-page flow using routing

```jsx
// App.jsx
import { Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import Todo from "./pages/Todo";
import About from "./pages/About";

function App() {
  return (
    <>
      <nav>
        <Link to="/">Home</Link> | <Link to="/todo">Todo</Link> |{" "}
        <Link to="/about">About</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/todo" element={<Todo />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </>
  );
}

export default App;
```

Remember to wrap `<App />` in `<BrowserRouter>` inside `main.jsx`.

## 5. Focus on clean component structure

**Suggested folder structure:**

```
src/
  components/     -> small reusable pieces (ProfileCard, Navbar, Button)
  pages/          -> one component per page (Home, Todo, About)
  App.jsx         -> routes and layout
  main.jsx        -> entry point
```

**Clean structure habits:**
- One component per file, with the file named after the component
- Component names start with a capital letter
- Keep components small and focused on one job
- Pass data through props instead of repeating code
- Put page-level components in `pages/` and reusable pieces in `components/`
