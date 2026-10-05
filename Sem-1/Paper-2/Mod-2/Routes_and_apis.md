# Create Routes and APIs

## 1. Building GET, POST, PUT, DELETE Endpoints

These four methods map directly to CRUD operations (same as the MongoDB methods you already know).

```js
const express = require("express");
const app = express();
app.use(express.json());

let users = [{ id: 1, name: "Adhul" }];

// GET — read data
app.get("/users", (req, res) => {
  res.json(users);
});

// POST — create data
app.post("/users", (req, res) => {
  const newUser = { id: users.length + 1, name: req.body.name };
  users.push(newUser);
  res.status(201).json(newUser);
});

// PUT — update data
app.put("/users/:id", (req, res) => {
  const id = Number(req.params.id);
  const user = users.find(u => u.id === id);
  if (user) {
    user.name = req.body.name;
    res.json(user);
  } else {
    res.status(404).json({ message: "User not found" });
  }
});

// DELETE — remove data
app.delete("/users/:id", (req, res) => {
  const id = Number(req.params.id);
  users = users.filter(u => u.id !== id);
  res.json({ message: "User deleted" });
});

app.listen(3000, () => console.log("Server running on port 3000"));
```

---

## 2. Understanding RESTful API Structure

**REST** is a convention for structuring APIs predictably, using URLs that represent *resources* (nouns), and HTTP methods that represent *actions* (verbs).

**Good REST structure:**
```
GET    /users          → get all users
GET    /users/5        → get user with id 5
POST   /users          → create a new user
PUT    /users/5        → update user with id 5
DELETE /users/5        → delete user with id 5
```

**Avoid this (not RESTful):**
```
GET /getAllUsers
GET /deleteUser?id=5
```
The URL should describe *what* resource you're working with — the HTTP method already tells you the action.

`req.params` is how you access values from the URL itself (like `:id` above).

---

## 3. Sending and Receiving JSON Data

**Receiving JSON (from the client, in the request body):**
```js
app.use(express.json()); // required middleware to parse JSON bodies

app.post("/users", (req, res) => {
  console.log(req.body); // { name: "Riya" }
});
```

**Sending JSON (response back to the client):**
```js
app.get("/users", (req, res) => {
  res.json({ message: "Success", data: users });
});
```

**Testing your API without a frontend:**
Use a tool like **Postman** or **Thunder Client** (VS Code extension) to send test requests (GET, POST, etc.) to your routes and see the responses — essential for backend development since there's no visual interface yet.
