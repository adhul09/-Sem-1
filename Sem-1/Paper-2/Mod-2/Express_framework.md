# Understand Express Framework

## 1. Why Express is Used

Building servers with just the built-in `http` module gets messy quickly — manually checking `req.url` for every route, parsing data manually, etc.

**Express** is a lightweight framework built on top of Node.js that makes building servers much simpler:
- Easy routing (`app.get`, `app.post`, etc.)
- Built-in and custom middleware support
- Simplified request/response handling
- Huge ecosystem of plugins and community support

It's the most widely used backend framework in the Node.js world, and a core part of the **MERN** stack (the "E" in MERN).

---

## 2. Setting Up an Express Application

**Install Express:**
```bash
npm install express
```

**Basic setup:**
```js
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Hello from Express!");
});

app.listen(3000, () => {
  console.log("Server running on http://localhost:3000");
});
```

Compare this to the raw `http` module version — no manual `req.url` checking needed, `app.get()` handles routing directly.

---

## 3. Understanding Routing and Middleware

### Routing
Routing defines what happens for different URLs and HTTP methods.

```js
app.get("/", (req, res) => {
  res.send("Home Page");
});

app.get("/about", (req, res) => {
  res.send("About Page");
});

app.post("/users", (req, res) => {
  res.send("User created");
});
```
Each route matches a specific **method** (GET, POST, etc.) and **path** (`/`, `/about`, `/users`).

### Middleware
Middleware are functions that run **in between** receiving a request and sending a response — used for tasks like logging, authentication, or parsing data.

```js
app.use((req, res, next) => {
  console.log(`${req.method} request to ${req.url}`);
  next(); // passes control to the next middleware/route
});
```

**Key point:** `next()` must be called, or the request will hang forever without a response.

**Common use case — parsing JSON data sent in requests:**
```js
app.use(express.json());

app.post("/users", (req, res) => {
  console.log(req.body); // now works, thanks to express.json()
  res.send("User data received");
});
```

**Simple way to think about it:** Routing decides *where* a request goes. Middleware decides what happens *along the way*, before it reaches its final destination.
