# Work with Node.js Basics

## 1. Running JavaScript Outside the Browser

Normally, JavaScript only ran inside browsers. Node.js changed that by providing a **runtime environment** that lets JS run directly on your computer/server.

**Running a file with Node.js:**
```bash
node app.js
```

**Simple example (app.js):**
```js
console.log("Hello from Node.js!");

const name = "Adhul";
console.log(`Welcome, ${name}`);
```
Run it with `node app.js` in your terminal, and it executes just like browser JS — but with no browser involved, and no `window` or `document` objects (since those are browser-specific).

---

## 2. Modules and File Structure

Node.js lets you split code across multiple files using **modules**, and connect them with `require` or `import`/`export`.

**Exporting from a file (math.js):**
```js
function add(a, b) {
  return a + b;
}

module.exports = add;
```

**Importing in another file (app.js):**
```js
const add = require("./math.js");
console.log(add(2, 3)); // 5
```

**Exporting multiple things:**
```js
// utils.js
module.exports = {
  add: (a, b) => a + b,
  subtract: (a, b) => a - b,
};
```
```js
// app.js
const { add, subtract } = require("./utils.js");
```

**Typical basic file structure:**
```
project/
  app.js         → main entry file
  routes/        → route files
  models/        → database models
  controllers/   → logic for handling requests
  package.json   → project configuration
```

---

## 3. Using Built-in Modules

Node.js comes with several modules already built in — no installation needed.

**Common built-in modules:**

```js
// File system — read/write files
const fs = require("fs");
fs.writeFileSync("notes.txt", "Hello file!");
const data = fs.readFileSync("notes.txt", "utf-8");
console.log(data);
```

```js
// Path — handle file paths safely across OS
const path = require("path");
console.log(path.join(__dirname, "files", "data.txt"));
```

```js
// OS — get system info
const os = require("os");
console.log(os.platform()); // e.g. "win32", "linux"
```

```js
// HTTP — create a web server (used heavily later)
const http = require("http");
```

**Quick note:** `require` is the older (CommonJS) way of importing. Newer projects sometimes use `import`/`export` (ES Modules) instead — but `require` is still extremely common in Node.js, especially in Express projects.
