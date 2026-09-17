# Asynchronous JavaScript

JavaScript normally runs code line by line (synchronously). But some things take time — like fetching data from a server. Asynchronous JS lets your code "wait" for that without freezing everything else.

## a. Callback Functions

A callback is simply a function passed into another function, to be run *later* (often after something finishes).

```js
function greet(name, callback) {
  console.log("Hi " + name);
  callback();
}

greet("Adhul", () => {
  console.log("This runs after the greeting");
});
```

**Real example** — `setTimeout` waits, then runs the callback:
```js
setTimeout(() => {
  console.log("This runs after 2 seconds");
}, 2000);
```

Problem with callbacks: too many nested callbacks become messy — known as "callback hell." This is why Promises were introduced.

---

## b. Promises (Basic Understanding)

A **Promise** represents a value that will be available *later* — either successfully (`resolve`) or with an error (`reject`).

```js
const myPromise = new Promise((resolve, reject) => {
  let success = true;
  if (success) {
    resolve("Data loaded!");
  } else {
    reject("Something went wrong");
  }
});

myPromise
  .then((result) => console.log(result))   // runs if resolved
  .catch((error) => console.log(error));   // runs if rejected
```

Think of a Promise like ordering food online — you get a "tracking status" immediately, even though the food (result) arrives later.

---

## c. async / await

`async/await` is a cleaner way to work with Promises — makes async code *look* synchronous, easier to read.

```js
async function loadData() {
  try {
    const response = await fetch("https://api.example.com/data");
    const data = await response.json();
    console.log(data);
  } catch (error) {
    console.log("Error fetching data:", error);
  }
}
```

- `async` before a function means it always returns a Promise
- `await` pauses execution *inside that function* until the Promise resolves
- Always pair with `try/catch` for error handling

---

## d. Handling Asynchronous Flows

**Running things one after another (sequential):**
```js
async function process() {
  const user = await getUser();
  const posts = await getPosts(user.id); // waits for user first
}
```

**Running things at the same time (parallel) — faster when tasks don't depend on each other:**
```js
async function loadAll() {
  const [users, posts] = await Promise.all([
    getUsers(),
    getPosts()
  ]);
}
```

**Simple rule of thumb:**
- Use `await` one after another only when the second task *needs* the result of the first
- Use `Promise.all()` when tasks are independent, to save time