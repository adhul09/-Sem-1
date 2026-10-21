# Understanding Modern JavaScript (ES6+) for React

## 1. Arrow functions

A shorter way to write functions. React components and event handlers use them constantly.

```js
// Normal function
function add(a, b) {
  return a + b;
}

// Arrow function
const add2 = (a, b) => a + b;

// One parameter, no brackets needed
const double = n => n * 2;
```

## 2. Destructuring

Pulls values out of objects or arrays into separate variables. In React it is mostly used on **props**.

```js
const user = { name: "Adhul", age: 18 };
const { name, age } = user;

const colors = ["red", "green"];
const [first, second] = colors;
```

```jsx
// Destructuring props directly in the parameter
function Greeting({ name }) {
  return <h1>Hello, {name}</h1>;
}
```

## 3. map

Creates a **new array** by transforming every item. In React it is used to render lists.

```js
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2);
console.log(doubled); // [2, 4, 6]
```

## 4. filter

Creates a **new array** with only the items that pass a condition.

```js
const nums = [1, 2, 3, 4, 5];
const even = nums.filter(n => n % 2 === 0);
console.log(even); // [2, 4]
```

## 5. reduce

Combines all items into a **single value**.

```js
const nums = [1, 2, 3, 4];
const total = nums.reduce((sum, n) => sum + n, 0);
console.log(total); // 10
```

`sum` is the running total, `n` is the current item, and `0` is the starting value.

## 6. Import and Export

Splits code across files.

**Named export** (can have many per file, imported with `{ }`):

```js
// utils.js
export const add = (a, b) => a + b;
export const PI = 3.14;

// App.jsx
import { add, PI } from "./utils.js";
```

**Default export** (one per file, imported without `{ }`):

```jsx
// Button.jsx
export default function Button() {
  return <button>Click</button>;
}

// App.jsx
import Button from "./Button.jsx";
```

**Note:** in React, component names must start with a capital letter.
