# Build Your First Server

## 1. Creating a Basic HTTP Server

Node.js has a built-in `http` module that lets you create a web server without any external packages.

```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.end("Hello, this is my first server!");
});

server.listen(3000, () => {
  console.log("Server running on http://localhost:3000");
});
```

Run it with:
```bash
node app.js
```
Then open `http://localhost:3000` in your browser — you'll see the message.

---

## 2. Understanding Request and Response Handling

Every time a browser (or any client) hits your server, Node.js gives you two objects:

- **`req` (request)** — information about what the client is asking for
- **`res` (response)** — what you send back to the client

```js
const server = http.createServer((req, res) => {
  console.log(req.url);     // e.g. "/" or "/about"
  console.log(req.method);  // "GET", "POST", etc.

  res.statusCode = 200;              // success status
  res.setHeader("Content-Type", "text/plain");
  res.end("Response sent!");
});
```

**Handling different routes manually:**
```js
const server = http.createServer((req, res) => {
  if (req.url === "/") {
    res.end("Welcome to Home Page");
  } else if (req.url === "/about") {
    res.end("This is the About Page");
  } else {
    res.statusCode = 404;
    res.end("Page not found");
  }
});
```
This works, but gets messy fast as routes grow — this is exactly the problem **Express** (covered next) solves.

---

## 3. How Servers Listen and Respond

`server.listen(port, callback)` tells Node.js to:
1. Start the server
2. Keep it running, actively "listening" for incoming requests on that port
3. Run the callback once it's successfully started

```js
server.listen(3000, () => {
  console.log("Server is listening on port 3000");
});
```

**Key points:**
- A **port** is like a specific "door" on your computer that the server listens through (3000, 5000, 8080 are common choices for development)
- The server keeps running continuously in the terminal — it doesn't stop after one request, it keeps handling new ones as they come in
- To stop it, press `Ctrl + C` in the terminal

**Full working example:**
```js
const http = require("http");

const server = http.createServer((req, res) => {
  res.setHeader("Content-Type", "text/plain");
  res.end(`You requested: ${req.url}`);
});

server.listen(3000, () => {
  console.log("Server running at http://localhost:3000");
});
```
