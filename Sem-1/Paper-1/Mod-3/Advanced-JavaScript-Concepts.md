# Advanced JavaScript Concepts

## a. Higher-Order Functions

A **higher-order function** is a function that either:
- takes another function as an argument, OR
- returns a function

You've already used these! `map`, `filter`, `reduce`, `forEach` are all higher-order functions.

```js
function greetGenerator(greeting) {
  return function (name) {
    console.log(`${greeting}, ${name}!`);
  };
}

const sayHello = greetGenerator("Hello");
sayHello("Adhul"); // "Hello, Adhul!"
```
Here, `greetGenerator` returns a new function — that's what makes it "higher-order."

---

## b. Closures in Practical Usage

A **closure** happens when a function "remembers" the variables from where it was created, even after that outer function has finished running.

```js
function counter() {
  let count = 0;
  return function () {
    count++;
    console.log(count);
  };
}

const increment = counter();
increment(); // 1
increment(); // 2
increment(); // 3
```
Even though `counter()` already finished running, the inner function still remembers `count` — that's a closure. It's commonly used to create private variables (similar to encapsulation).

**Practical use case:** a simple click counter on a button
```js
function clickCounter() {
  let clicks = 0;
  return () => {
    clicks++;
    console.log(`Button clicked ${clicks} times`);
  };
}
const handleClick = clickCounter();
button.addEventListener("click", handleClick);
```

---

## c. Generator Functions (Basic Idea)

A **generator function** can pause and resume — it doesn't run all at once like a normal function. Defined with `function*` and uses `yield` to pause.

```js
function* numberGenerator() {
  yield 1;
  yield 2;
  yield 3;
}

const gen = numberGenerator();
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
console.log(gen.next().value); // 3
```
Each call to `.next()` resumes the function until the next `yield`. You won't use these often as a beginner, but it's good to know they exist — useful for handling large data sequences one piece at a time.

---

## d. Writing Reusable and Maintainable Logic

A few simple habits that make code easier to reuse and maintain:

**1. Keep functions small and focused (do one thing):**
```js
// Instead of one giant function doing everything...
function processOrder(order) {
  validateOrder(order);
  calculateTotal(order);
  saveOrder(order);
}
```

**2. Avoid repeating yourself (DRY principle):**
```js
// Bad: repeated logic
const tax1 = price1 * 0.1;
const tax2 = price2 * 0.1;

// Good: reusable function
function calculateTax(price) {
  return price * 0.1;
}
```

**3. Use clear, descriptive names:**
```js
// Unclear
function calc(x) { ... }

// Clear
function calculateMonthlyInterest(principal) { ... }
```

These habits matter more as your projects grow — code you can reuse and easily understand later (even by you, months from now) saves huge amounts of time.