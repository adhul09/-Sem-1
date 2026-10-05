# Handle Errors and Validation

## 1. Proper Error Handling in Express

**Wrap async route logic in try/catch:**
```js
app.get("/users/:id", async (req, res) => {
  try {
    const user = await User.findById(req.params.id);
    if (!user) {
      return res.status(404).json({ message: "User not found" });
    }
    res.json(user);
  } catch (error) {
    res.status(500).json({ message: "Server error", error: error.message });
  }
});
```

**Express error-handling middleware** (catches errors from anywhere in the app):
```js
app.use((err, req, res, next) => {
  console.error(err.stack);
  res.status(500).json({ message: "Something went wrong" });
});
```
This special middleware takes **4 parameters** (`err, req, res, next`) — Express recognizes this pattern specifically as an error handler, and it should be placed **after** all your routes.

---

## 2. Understanding Request Validation Basics

Validation means checking that incoming data is correct **before** using it or saving it to the database.

**Manual validation example:**
```js
app.post("/users", (req, res) => {
  const { name, age } = req.body;

  if (!name || typeof name !== "string") {
    return res.status(400).json({ message: "Valid name is required" });
  }
  if (!age || age < 0) {
    return res.status(400).json({ message: "Valid age is required" });
  }

  // proceed to save if validation passes
  res.status(201).json({ message: "User created" });
});
```

**Using a validation library (common in real projects) — example with `express-validator`:**
```bash
npm install express-validator
```
```js
const { body, validationResult } = require("express-validator");

app.post("/users",
  body("name").notEmpty().withMessage("Name is required"),
  body("age").isInt({ min: 0 }).withMessage("Valid age is required"),
  (req, res) => {
    const errors = validationResult(req);
    if (!errors.isEmpty()) {
      return res.status(400).json({ errors: errors.array() });
    }
    res.status(201).json({ message: "User created" });
  }
);
```

---

## 3. Building Structured API Responses

Keeping a **consistent response format** across your whole API makes it much easier for the frontend to handle responses predictably.

**Example consistent structure:**
```js
// Success
res.status(200).json({
  success: true,
  data: user,
  message: "User fetched successfully"
});

// Error
res.status(400).json({
  success: false,
  message: "Invalid request data"
});
```

**Common HTTP status codes to know:**
| Code | Meaning |
|---|---|
| 200 | OK — success |
| 201 | Created — new resource created |
| 400 | Bad Request — invalid input |
| 401 | Unauthorized — not logged in |
| 403 | Forbidden — no permission |
| 404 | Not Found |
| 500 | Server Error |

Using consistent status codes and response shapes makes your API predictable and much easier to debug and use.
