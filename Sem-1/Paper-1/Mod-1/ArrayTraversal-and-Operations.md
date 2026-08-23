# Understanding Array Traversal and Operations

## a. Iterating through arrays using loops

Array traversal means going through each element of an array one by one.

A `for` loop can be used to iterate through an array.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];

for (let i = 0; i < fruits.length; i++) {
  console.log(fruits[i]);
}
```

Output:

```text
Apple
Banana
Mango
```

Here, `i` represents the index of each element.

We can also use a `for...of` loop to directly access the values.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];

for (let fruit of fruits) {
  console.log(fruit);
}
```

## b. Input/output using arrays

Arrays can be used to store multiple inputs or values.

For example, values can be stored in an array and then accessed using indexes.

Eg:

```js
let numbers = [10, 20, 30, 40];

console.log(numbers[0]); // 10
console.log(numbers[2]); // 30
```

We can also add values to an array using methods such as `push()`.

Eg:

```js
let numbers = [];

numbers.push(10);
numbers.push(20);
numbers.push(30);

console.log(numbers);
```

Output:

```text
[10, 20, 30]
```

## c. Basic array operations

### i. push()

`push()` is used to add one or more elements to the **end** of an array.

Eg:

```js
let fruits = ["Apple", "Banana"];

fruits.push("Mango");

console.log(fruits);
```

Output:

```text
["Apple", "Banana", "Mango"]
```

### ii. pop()

`pop()` is used to remove the **last element** from an array.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];

fruits.pop();

console.log(fruits);
```

Output:

```text
["Apple", "Banana"]
```

### iii. shift()

`shift()` is used to remove the **first element** from an array.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];

fruits.shift();

console.log(fruits);
```

Output:

```text
["Banana", "Mango"]
```

### iv. unshift()

`unshift()` is used to add one or more elements to the **beginning** of an array.

Eg:

```js
let fruits = ["Banana", "Mango"];

fruits.unshift("Apple");

console.log(fruits);
```

Output:

```text
["Apple", "Banana", "Mango"]
```

The basic difference can be remembered as:

```text
push()    → adds to the end
pop()     → removes from the end
unshift() → adds to the beginning
shift()   → removes from the beginning
```

## d. Introduction to array methods

### i. map()

`map()` is used to create a new array by performing an operation on each element of an existing array, it accepts a user defined function as argument to map the existing array into new array.

Eg:

```js
let numbers = [1, 2, 3, 4];
function double(num) {
  return num * 2;
}

let doubled = numbers.map(double);

console.log(doubled);
```

Output:

```text
[2, 4, 6, 8]
```

Here, `map()` goes through each element and returns a new array containing the changed values.

### ii. filter()

`filter()` is used to create a new array containing only the elements that satisfy a condition, it accepts a user defined function containing the condition as argument to filter the existing array into new array.

Eg:

```js
let numbers = [1, 2, 3, 4, 5, 6];
function even(num) {
  return num % 2 === 0;
}

let evenNumbers = numbers.filter(even);

console.log(evenNumbers);
```

Output:

```text
[2, 4, 6]
```

Here, only the numbers that satisfy the condition are included in the new array.

### iii. reduce()

`reduce()` is used to reduce all the elements of an array into a single value, <br>it accepts a user defined function and an intial value (starting value of the accumulator) as argument to reduce the existing array into a new single value.

Eg:

```js
let numbers = [10, 20, 30, 40];
function reduced(total, num) {
  return total + num;
}

let sum = numbers.reduce(reduced, 0);

console.log(sum);
```

Output:

```text
100
```

Here, `reduce()` adds all the numbers together and returns a single value.

In simple terms:

```text
map()    → transforms every element → returns a new array
filter() → selects elements based on a condition → returns a new array
reduce() → combines elements → returns a single value
```
