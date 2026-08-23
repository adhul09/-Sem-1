# Apply Through Hands-on Tasks

## a. Build small logic-based programs

**Program to check whether a number is even or odd**

```js
let number = 10;

if (number % 2 === 0) {
  console.log("Even");
} else {
  console.log("Odd");
}
```

Output:

```text
Even
```

## b. Solve array and condition-based problems

**Find the sum of all even numbers in an array**

```js
let numbers = [1, 2, 3, 4, 5, 6];

let sum = 0;

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] % 2 === 0) {
    sum += numbers[i];
  }
}

console.log(sum);
```

Output:

```text
12
```

## c. Use functions to organize logic

Functions can be used to separate different parts of a program and make the logic reusable.

Eg:

```js
function isEven(number) {
  return number % 2 === 0;
}

console.log(isEven(10));
console.log(isEven(7));
```

Output:

```text
true
false
```

Here, the logic for checking whether a number is even is placed inside the `isEven()` function. The same function can be reused with different numbers.

## d. Practice writing readable and structured code

```js
// function
function calculateTotal(price, quantity) {
  let total = price * quantity;

  return total;
}
// declaring and initializing variables
let price = 100;                                
let quantity = 3;

let total = calculateTotal(price, quantity);    // calling function

console.log(total);                             // prints output
```

## e. Identify and fix logical mistakes

A logical mistake occurs when the code runs without a syntax error but produces an incorrect result because the logic is wrong.

Eg:

```js
let number = 5;

if (number % 2 === 0) {
  console.log("Odd");
} else {
  console.log("Even");
}
```

The code runs, but the output is incorrect because the messages in the `if` and `else` blocks are reversed.

Corrected code:

```js
let number = 5;

if (number % 2 === 0) {
  console.log("Even");
} else {
  console.log("Odd");
}
```

Output:

```text
Odd
```
