# Advanced Array & Data Handling

## a. Array Methods

### `map()` — transform every item
Creates a **new array** by transforming each element. Doesn't change the original.
```js
const nums = [1, 2, 3];
const doubled = nums.map(n => n * 2);
// doubled = [2, 4, 6]
```

### `filter()` — keep only what matches
Creates a **new array** with only the elements that pass a condition.
```js
const nums = [1, 2, 3, 4, 5];
const evens = nums.filter(n => n % 2 === 0);
// evens = [2, 4]
```

### `reduce()` — combine into one value
Takes an array and "reduces" it to a single value (sum, total, object, etc.)
```js
const nums = [1, 2, 3, 4];
const sum = nums.reduce((total, n) => total + n, 0);
// sum = 10
```
`0` here is the starting value of `total`.

### `find()` — get the first match
Returns the **first element** that matches a condition (not an array, just one item).
```js
const nums = [5, 12, 8, 20];
const found = nums.find(n => n > 10);
// found = 12
```

### `forEach()` — just loop, no new array
Runs a function for each item. Used for side effects (like printing), not for creating new data.
```js
const nums = [1, 2, 3];
nums.forEach(n => console.log(n));
// prints 1, 2, 3
```

**Quick way to remember:**
| Method    | Returns              | Use when you want to... |
|-----------|----------------------|--------------------------|
| map       | new array (same size)| transform each item      |
| filter    | new array (smaller)  | keep some items           |
| reduce    | single value          | combine into one result   |
| find      | one item              | search for one match      |
| forEach   | nothing (undefined)   | just loop/do something    |

---

## b. String and Number Methods

**Common String methods:**
```js
"Hello".toUpperCase()     // "HELLO"
"Hello".toLowerCase()     // "hello"
"Hello World".includes("World")  // true
"Hello".slice(1, 3)       // "el"
"  hi  ".trim()           // "hi"
"a,b,c".split(",")        // ["a", "b", "c"]
```

**Common Number methods:**
```js
Number("42")          // 42 (convert string to number)
(3.14159).toFixed(2)  // "3.14" (round to 2 decimals)
Number.isInteger(5)   // true
Math.round(4.7)       // 5
Math.max(1, 5, 3)     // 5
```

---

## c. Set and Map

### `Set` — a list with no duplicates
```js
const mySet = new Set([1, 2, 2, 3]);
// mySet = {1, 2, 3} → duplicates auto-removed
mySet.add(4);
mySet.has(2);   // true
```
Useful for quickly removing duplicate values from an array:
```js
const arr = [1, 1, 2, 3, 3];
const unique = [...new Set(arr)]; // [1, 2, 3]
```

### `Map` — like an object, but better for key-value pairs
```js
const myMap = new Map();
myMap.set("name", "Adhul");
myMap.set("age", 20);

myMap.get("name");   // "Adhul"
myMap.has("age");    // true
```
Difference from a regular object: Map keys can be *any* type (not just strings), and it keeps order reliably.

---

## d. Data Transformation & Manipulation Patterns

A common real-world pattern: **filter → map → reduce**, done in a chain.

```js
const products = [
  { name: "Pen", price: 10, inStock: true },
  { name: "Bag", price: 500, inStock: false },
  { name: "Book", price: 150, inStock: true },
];

const total = products
  .filter(p => p.inStock)        // only in-stock items
  .map(p => p.price)             // get just the prices
  .reduce((sum, price) => sum + price, 0); // add them up

// total = 160
```

This chaining pattern (filter → map → reduce) is extremely common in real projects — get used to reading it left to right: "filter this, then transform it, then combine it."