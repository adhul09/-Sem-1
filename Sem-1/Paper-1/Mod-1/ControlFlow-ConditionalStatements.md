# Understanding Control Flow - Conditional Statements

## a. if, if-else, else if

**if:**

Used to execute a block of code only when a condition is true.

Eg:

```js
let age = 18;

if (age >= 18) {
  console.log("Eligible");
}
```

**if-else:**

Used when there are two possible outcomes. If the condition is true, `if` block runs, otherwise `else` block runs.

Eg:

```js
let age = 16;

if (age >= 18) {
  console.log("Eligible");
} else {
  console.log("Not Eligible");
}
```

**else if:**

Used to check multiple conditions one after another.

Eg:

```js
let mark = 75;

if (mark >= 90) {
  console.log("A");
} else if (mark >= 75) {
  console.log("B");
} else {
  console.log("C");
}
```

## b. Nested conditions

A condition placed inside another condition is called a nested condition.

Eg:

```js
let age = 20;
let hasID = true;

if (age >= 18) {
  if (hasID) {
    console.log("Allowed");
  }
}
```

## c. switch statement

Used to execute different blocks of code based on the value of an expression.

Eg:

```js
let day = 2;

switch (day) {
  case 1:
    console.log("Monday");
    break;

  case 2:
    console.log("Tuesday");
    break;

  case 3:
    console.log("Wednesday");
    break;

  default:
    console.log("Invalid day");
}
```

`break` is used to stop the execution of the next cases after a matching case is found.

`default` runs when none of the cases match.

# d. Ternary operator

A shorter way of writing a simple `if-else` condition.

Syntax:

```js
condition ? valueIfTrue : valueIfFalse;
```

Eg:

```js
let age = 20;

let result = age >= 18 ? "Eligible" : "Not Eligible";

console.log(result); // Eligible
```

Here, if the condition is true, `"Eligible"` is assigned to `result`, otherwise `"Not Eligible"` is assigned.
