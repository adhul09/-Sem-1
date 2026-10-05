# Connect Node.js with MongoDB

## 1. How the Backend Connects to the Database

The typical flow:
```
Client (React) → Express Route → Mongoose Model → MongoDB Database
```

Your Express server acts as the middleman — it receives requests from the frontend, talks to MongoDB to get/save data, and sends a response back.

---

## 2. Using MongoDB with Node.js (via Mongoose)

**Mongoose** is an ODM (Object Data Modeling) library that makes working with MongoDB in Node.js much easier — it lets you define schemas (structure) for your data, even though MongoDB itself is schema-less.

**Install Mongoose:**
```bash
npm install mongoose
```

**Connect to MongoDB:**
```js
const mongoose = require("mongoose");

mongoose.connect("mongodb://localhost:27017/myDatabase")
  .then(() => console.log("MongoDB connected"))
  .catch((err) => console.log("Connection error:", err));
```

**Define a Schema and Model:**
```js
const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
  email: String,
});

const User = mongoose.model("User", userSchema);
```
The `User` model is now your interface for interacting with the `users` collection in MongoDB.

---

## 3. Performing CRUD Operations from the Backend

**Create:**
```js
app.post("/users", async (req, res) => {
  const newUser = new User(req.body);
  await newUser.save();
  res.status(201).json(newUser);
});
```

**Read:**
```js
app.get("/users", async (req, res) => {
  const users = await User.find();
  res.json(users);
});
```

**Update:**
```js
app.put("/users/:id", async (req, res) => {
  const updatedUser = await User.findByIdAndUpdate(req.params.id, req.body, { new: true });
  res.json(updatedUser);
});
```

**Delete:**
```js
app.delete("/users/:id", async (req, res) => {
  await User.findByIdAndDelete(req.params.id);
  res.json({ message: "User deleted" });
});
```

**Key points:**
- All Mongoose database operations are **asynchronous** — always use `async/await` (ties directly back to what you learned about Promises/async-await earlier)
- `{ new: true }` in `findByIdAndUpdate` makes it return the *updated* document, not the old one
- Wrap these in `try/catch` in real projects to handle database errors properly (covered next)
