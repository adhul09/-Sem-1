# Structure a Scalable Backend

## 1. Organizing Code Using MVC Pattern

**MVC** = Model, View, Controller. In a backend API (no actual "view" since the frontend handles that), it's mostly **Model + Controller + Routes**.

- **Model** — defines the data structure (Mongoose schemas)
- **Controller** — contains the actual logic for handling requests
- **Routes** — define which URL triggers which controller function

This keeps things organized instead of cramming everything into one giant file.

---

## 2. Separating Routes, Controllers, and Models

**Typical folder structure:**
```
project/
  models/
    userModel.js
  controllers/
    userController.js
  routes/
    userRoutes.js
  app.js
```

**models/userModel.js:**
```js
const mongoose = require("mongoose");

const userSchema = new mongoose.Schema({
  name: String,
  age: Number,
});

module.exports = mongoose.model("User", userSchema);
```

**controllers/userController.js:**
```js
const User = require("../models/userModel");

exports.getUsers = async (req, res) => {
  const users = await User.find();
  res.json(users);
};

exports.createUser = async (req, res) => {
  const newUser = new User(req.body);
  await newUser.save();
  res.status(201).json(newUser);
};
```

**routes/userRoutes.js:**
```js
const express = require("express");
const router = express.Router();
const { getUsers, createUser } = require("../controllers/userController");

router.get("/", getUsers);
router.post("/", createUser);

module.exports = router;
```

**app.js (main file):**
```js
const express = require("express");
const app = express();
const userRoutes = require("./routes/userRoutes");

app.use(express.json());
app.use("/users", userRoutes);

app.listen(3000, () => console.log("Server running"));
```

---

## 3. Maintaining a Clean and Readable Project Structure

**Why this structure matters:**
- Easy to find things — routes, logic, and data models each have their own clear place
- Easier to scale — adding a new feature (e.g., "products") just means adding a new model/controller/route set, following the same pattern
- Easier to debug — if something's wrong with how users are created, you know to check `userController.js`, not search through one massive file

**General rule of thumb:**
- **Routes** = "where does this request go?"
- **Controllers** = "what should happen when it gets there?"
- **Models** = "what does the data look like?"

Keeping these three responsibilities separate is one of the most important habits for writing backend code that stays manageable as a project grows.
