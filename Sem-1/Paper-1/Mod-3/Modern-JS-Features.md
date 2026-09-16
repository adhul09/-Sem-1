# Modern JavaScript Features (ES6+)

## a. Destructuring

Destructuring lets you extract values from arrays or objects into individual variables, in a shorter syntax.

**Array destructuring:**
```javascript
let colors = ["red", "green", "blue"];
let [first, second, third] = colors;

console.log(first);  // "red"
console.log(second); // "green"
```

**Object destructuring:**
```javascript
let user = { name: "Adhul", age: 18 };
let { name, age } = user;

console.log(name); // "Adhul"
console.log(age);  // 18
```

Without destructuring, you'd have to write `user.name`, `user.age` separately — destructuring pulls them out into their own variables directly.

## b. Spread and rest operators

Both use `...` (three dots), but do opposite things depending on context.

**Spread** — expands an array/object into individual elements.

```javascript
let arr1 = [1, 2, 3];
let arr2 = [...arr1, 4, 5];
console.log(arr2); // [1, 2, 3, 4, 5]

let obj1 = { a: 1, b: 2 };
let obj2 = { ...obj1, c: 3 };
console.log(obj2); // { a: 1, b: 2, c: 3 }
```

**Rest** — collects multiple remaining elements into a single array (used in function parameters or destructuring).

```javascript
function sum(...numbers) {
  return numbers.reduce((total, n) => total + n, 0);
}

console.log(sum(1, 2, 3, 4)); // 10
```

**Simple way to tell them apart:** spread **expands** things out, rest **collects** things together.

## c. Optional chaining

Optional chaining (`?.`) safely accesses nested object properties, without throwing an error if something in the chain doesn't exist.

```javascript
let user = {
  name: "Adhul",
  address: {
    city: "Chalakudy"
  }
};

console.log(user.address?.city);   // "Chalakudy"
console.log(user.contact?.phone);  // undefined (no error, even though "contact" doesn't exist)
```

Without `?.`, trying `user.contact.phone` when `contact` doesn't exist would throw a `TypeError` and crash the script. `?.` just returns `undefined` safely instead.

## d. Short-circuiting

Short-circuiting means an expression stops evaluating as soon as the result is already determined.

### i. `||` (OR)
Returns the first **truthy** value, or the last value if none are truthy. Commonly used for default values.

```javascript
let name = "" || "Guest";
console.log(name); // "Guest" (empty string is falsy, so it moves to the next value)
```

### ii. `&&` (AND)
Returns the first **falsy** value, or the last value if all are truthy. Commonly used to conditionally run code.

```javascript
let isLoggedIn = true;
isLoggedIn && console.log("Welcome back!"); // runs, since isLoggedIn is truthy
```

### iii. `??` (Nullish coalescing)
Similar to `||`, but only falls back if the value is `null` or `undefined` — NOT for other falsy values like `0` or `""`.

```javascript
let score = 0;
console.log(score || 10);  // 10 (0 is falsy, so || falls back)
console.log(score ?? 10);  // 0  (0 is not null/undefined, so ?? keeps it)
```



## e. Enhanced object literals

ES6 introduced shorter syntax for writing objects.

**Shorthand property names** — if a variable name matches the key you want, you can skip repeating it:

```javascript
let name = "Adhul";
let age = 18;

// Old way
let user = { name: name, age: age };

// Shorthand (ES6)
let user2 = { name, age };
```

**Shorthand method names** — skip the `function` keyword inside objects:

```javascript
// Old way
let obj = {
  greet: function() {
    console.log("Hi");
  }
};

// Shorthand (ES6)
let obj2 = {
  greet() {
    console.log("Hi");
  }
};
```

## f. Modules (import/export)

Modules let you split code across multiple files, and share functions/variables between them.

**Exporting from a file** (`math.js`):
```javascript
export function add(a, b) {
  return a + b;
}

export const PI = 3.14;
```

**Importing into another file** (`main.js`):
```javascript
import { add, PI } from './math.js';

console.log(add(2, 3)); // 5
console.log(PI);         // 3.14
```

**Default export** (one main thing per file):
```javascript
// math.js
export default function add(a, b) {
  return a + b;
}

// main.js
import add from './math.js';
```

**Why modules matter:** they let you organize large codebases into smaller, manageable files instead of one giant file — this is exactly how React/Node projects are structured, with each component/function typically living in its own file.