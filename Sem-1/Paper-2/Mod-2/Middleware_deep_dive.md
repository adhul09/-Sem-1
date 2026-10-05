# Understand Middleware Deeply

## 1. How Middleware Works in Express

Middleware functions sit **between** the request coming in and the final route handler. They have access to `req`, `res`, and a special function called `next()`.

```js
app.use((req, res, next) => {
  console.log("Middleware ran!");
  next(); // without this, the request gets stuck here forever
});
```

**The request flow looks like this:**
```
Request → Middleware 1 → Middleware 2 → Route Handler → Response
```

Each middleware can:
- Run code
- Modify `req`/`res`
- End the request-response cycle, OR
- Call `next()` to pass control forward

**Example — a middleware that blocks the request:**
```js
app.use((req, res, next) => {
  if (!req.headers.authorization) {
    return res.status(401).json({ message: "Not authorized" }); // stops here, no next()
  }
  next(); // only continues if authorized
});
```

---

## 2. Using Built-in Middleware

Express comes with some middleware ready to use:

```js
// Parses incoming JSON request bodies
app.use(express.json());

// Parses URL-encoded form data
app.use(express.urlencoded({ extended: true }));

// Serves static files (images, CSS, HTML) from a folder
app.use(express.static("public"));
```

With `express.static("public")`, any file inside a `public` folder becomes directly accessible in the browser (e.g., `public/logo.png` → `http://localhost:3000/logo.png`).

---

## 3. Creating Custom Middleware

You can write your own middleware for tasks specific to your app — logging, authentication checks, timestamps, etc.

**Simple logger middleware:**
```js
function logger(req, res, next) {
  console.log(`[${new Date().toISOString()}] ${req.method} ${req.url}`);
  next();
}

app.use(logger);
```

**Middleware for a specific route only:**
```js
function checkAdmin(req, res, next) {
  if (req.headers.role !== "admin") {
    return res.status(403).json({ message: "Admins only" });
  }
  next();
}

app.delete("/users/:id", checkAdmin, (req, res) => {
  res.send("User deleted by admin");
});
```
Here, `checkAdmin` runs **before** the actual delete logic — only proceeding if the check passes.

**Order matters:** Middleware runs in the exact order it's defined. Always place `express.json()` and similar setup middleware near the top of your file, before your routes.
