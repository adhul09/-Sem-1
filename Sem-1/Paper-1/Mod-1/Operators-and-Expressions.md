# Understanding Operators and Expressions

## a. Arithmetic, relational, and logical operators

**Arithmetic operators:**
Used to perform mathematical operations

* `+` Addition
* `-` Subtraction
* `*` Multiplication
* `/` Division
* `%` Remainder
* `**` Exponentiation

Eg:

```js
let x = 10;
let y = 3;

console.log(x + y); // 13
console.log(x - y); // 7
console.log(x * y); // 30
console.log(x / y); // 3.33
console.log(x % y); // 1
console.log(x ** y); // 1000
```

**Relational operators:**

Used to compare two values and returns `true` or `false`

* `>` Greater than
* `<` Less than
* `>=` Greater than or equal to
* `<=` Less than or equal to
* `===` Strictly equal
* `!==` Strictly not equal

Eg:

```js
let x = 10;
let y = 5;

console.log(x > y); // true
console.log(x < y); // false
console.log(x === y); // false
```

**Logical operators:**
Used to combine or reverse conditions

* `&&` AND - returns true if both conditions are true
* `||` OR - returns true if at least one condition is true
* `!` NOT - reverses the result

Eg:

```js
let age = 20;
let hasID = true;

console.log(age >= 18 && hasID); // true
console.log(age < 18 || hasID); // true
console.log(!hasID); // false
```

## b. Assignment operators

Used to assign or update values in a variable

* `=` Assigns a value
* `+=` Adds and assigns
* `-=` Subtracts and assigns
* `*=` Multiplies and assigns
* `/=` Divides and assigns

Eg:

```js
let x = 10;

x += 5; // x = 15
x -= 3; // x = 12
x *= 2; // x = 24
x /= 4; // x = 6
```

## c. Increment/decrement

**Increment (`++`):**
Increases the value by 1

Eg:

```js
let x = 5;

x++;
console.log(x); // 6
```

**Decrement (`--`):**
Decreases the value by 1

Eg:

```js
let x = 5;

x--;
console.log(x); // 4
```


**## d. Operator precedence and evaluation**

Operator precedence determines the order in which operators are evaluated. It is similar to PEMDAS in mathematics.

***P -  Parentheses (),<br>E - Exponents,<br> M - Multiplication *,<br> D - Division /,<br> A - Addition +,<br>S - Subtraction -****

Eg:

```js
let x = 2 + 3 * 4;

console.log(x); // 14.
