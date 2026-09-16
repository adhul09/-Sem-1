# JavaScript Core Concepts

## a. Arrays, objects, and functions in depth

**Arrays** — ordered collections of values, with many built-in methods for manipulation.

```javascript
let fruits = ["apple", "banana", "mango"];

fruits.push("orange");      // adds to end
fruits.pop();                // removes from end
fruits.length;                // 3
fruits[0];                    // "apple"
```

**Objects** — collections of key-value pairs, representing structured data.

```javascript
let user = {
  name: "Adhul",
  age: 18,
  greet: function() {
    console.log("Hello, " + this.name);
  }
};

user.greet(); // "Hello, Adhul"
```
Objects can hold not just values, but also functions (called **methods** when they belong to an object).

**Functions** — reusable blocks of code that perform a task, can accept inputs (parameters) and return outputs.

```javascript
function add(a, b) {
  return a + b;
}

console.log(add(2, 3)); // 5
```

**Function types worth knowing:**
```javascript
// Function declaration
function greet() { console.log("Hi"); }

// Function expression
const greet2 = function() { console.log("Hi"); };

// Arrow function (shorter syntax, ES6+)
const greet3 = () => console.log("Hi");
```

## b. Reference vs value behavior

This is about **how JavaScript stores and copies different data types.**

**Primitives (string, number, boolean, null, undefined)** are stored **by value** — copying them creates a completely independent copy.

```javascript
let a = 5;
let b = a;   // b gets a copy of a's value
b = 10;

console.log(a); // 5 (unaffected)
console.log(b); // 10
```

**Objects and arrays** are stored **by reference** — copying them just copies the *address/reference* pointing to the same underlying data, not a separate copy.

```javascript
let obj1 = { name: "Adhul" };
let obj2 = obj1;   // obj2 points to the SAME object as obj1

obj2.name = "Rema";

console.log(obj1.name); // "Rema" (changed too! same object)
```



## c. Scope and execution context

**Scope** determines **where a variable can be accessed** in your code.

**Global scope** — accessible from anywhere in the code
```javascript
let x = 10; // global

function show() {
  console.log(x); // accessible here too
}
```

**Function scope** — variables declared inside a function are only accessible within that function
```javascript
function show() {
  let y = 20; // function-scoped
}
console.log(y); // ReferenceError - not accessible outside
```

**Block scope** — `let`/`const` declared inside `{ }` (like `if`, `for`) are only accessible within that block
```javascript
if (true) {
  let z = 30; // block-scoped
}
console.log(z); // ReferenceError
```
### Execution Context & Call Stack

When JS code runs, it creates an **Execution Context** — a container 
with two parts: **Memory** (stores variables/functions) and **Code** 
(runs line by line). The first one created is the **Global Execution 
Context**.

**Created in 2 phases:**
1. **Memory phase** — variables set to `undefined`, functions stored fully
2. **Execution phase** — code runs line by line, real values assigned

Every function call creates a **new execution context** the same way. 
When `return` is hit, control goes back to the caller and that context 
is removed.

**Call Stack** tracks the order of execution contexts based on LIFO (last in, first out)      principle:
1. Global context goes in first
2. Each function call adds a context on top
3. Finished functions are popped off
4. Global context is removed last.


## d. Hoisting and closures

### <u>Hoisting</u>

JavaScript moves variable and function declarations to the top of their scope (conceptually) during the memory creation phase, before code actually runs.

```javascript
console.log(a); // undefined (not an error - hoisted, but not yet assigned)
var a = 5;

sayHi(); // works! function declarations are fully hoisted
function sayHi() {
  console.log("Hi");
}
```

`let`/`const` are hoisted too, but stay in the "Temporal Dead Zone" — accessing them before their declaration line throws an error instead of returning `undefined`.


***Hoisting is the behavior where declarations appear to be available before their position in the code is reached, because JavaScript sets up their bindings during the creation phase.***

### <u>Closures</u> 

***Function along with its lexical scope bundled together forms a closure.***

Eg:  a function that "remembers" the variables from where it was created, even after that outer function has finished running.

```javascript
function outer() {
  let count = 0;

  return function inner() {
    count++;
    console.log(count);
  };
}

let counter = outer();
counter(); // 1
counter(); // 2
counter(); // 3
```

Here, `inner()` keeps access to `count` even though `outer()` already finished executing. This is a closure — the inner function "closes over" the variable from its parent scope, keeping it alive for as long as the inner function exists.


