# Understanding Functions and Logical Thinking

## a. Function declaration and function expression

A function is a reusable block of code that performs a specific task.

### Function declaration

A function declaration is created using the `function` keyword followed by the function name.

Eg:

```js
function greet() {
  console.log("Hello");
}

greet();
```

Output:

```text
Hello
```

Here, `greet()` is used to call the function and execute the code inside it.

### Function expression

A function expression is when a function is assigned to a variable.

Eg:

```js
let greet = function () {
  console.log("Hello");
};

greet();
```

Output:

```text
Hello
```

Here, the function is stored inside the `greet` variable and can be called using `greet()`.

The main difference is that a **function declaration has a function name directly**, while a **function expression assigns a function to a variable**.

## b. Arrow functions

An arrow function is a shorter way of writing a function. It uses the `=>` symbol.

Eg:

```js
let greet = () => {
  console.log("Hello");
};

greet();
```

Output:

```text
Hello
```

An arrow function can also take parameters.

Eg:

```js
let double = (num) => {
  return num * 2;
};

console.log(double(5));
```

Output:

```text
10
```


## c. Parameters and return values

Parameters are variables given to a function so that it can receive values when it is called.

Eg:

```js
function add(a, b) {
  return a + b;
}

console.log(add(10, 20));
```

Output:

```text
30
```

Here, `a` and `b` are parameters.

When the function is called:

```js
add(10, 20);
```

`10` and `20` are the values passed to the parameters (Arguments).

The `return` statement is used to send a value back from the function.

Eg:

```js
function square(num) {
  return num * num;
}

let result = square(5);

console.log(result);
```

Output:

```text
25
```

Here, the function calculates the square and returns the result, which is stored in `result`.

## d. Breaking logic into reusable functions

Instead of writing all the code in one large block, we can divide the logic into smaller functions.

This makes the code easier to understand, reuse and maintain.

Eg:

```js
function calculateTotal(price, quantity) {
  return price * quantity;
}

function displayTotal(total) {
  console.log("Total:", total);
}

let total = calculateTotal(100, 3);

displayTotal(total);
```

Output:

```text
Total: 300
```

Here, `calculateTotal()` is responsible for calculating the total, while `displayTotal()` is responsible for displaying it.

The same function can also be reused with different values.
