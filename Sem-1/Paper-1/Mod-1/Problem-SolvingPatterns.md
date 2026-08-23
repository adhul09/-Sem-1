# Understanding Problem-Solving Patterns

## a. Searching elements (linear search)

Linear search is a simple searching method where each element of an array is checked one by one until the required element is found.

Eg:

```js
let numbers = [10, 20, 30, 40, 50];

let target = 30;
let found = false;

for (let i = 0; i < numbers.length; i++) {
  if (numbers[i] === target) {
    found = true;
    break;
  }
}

console.log(found);
```

Output:

```text
true
```

Here, the array is checked from the beginning, one element at a time. The `break` statement stops the loop when the target element is found.

## b. Reversing arrays

An array can be reversed so that its elements appear in the opposite order.

Eg:

```js
let numbers = [1, 2, 3, 4, 5];

numbers.reverse();

console.log(numbers);
```

Output:

```text
[5, 4, 3, 2, 1]
```

The `reverse()` method changes the order of the elements in the original array.

We can also reverse an array using a loop.

Eg:

```js
let numbers = [1, 2, 3, 4, 5];
let reversed = [];

for (let i = numbers.length - 1; i >= 0; i--) {
  reversed.push(numbers[i]);
}

console.log(reversed);
```

Output:

```text
[5, 4, 3, 2, 1]
```

## c. Basic sorting idea

Sorting means arranging elements in a particular order, such as ascending or descending order.

JavaScript provides the `sort()` method for sorting arrays.  
sort() takes a function as an argument.  

For numbers, a comparison function is generally used.

Eg:

```js
let numbers = [40, 10, 30, 20];

numbers.sort(function (a, b) {
  return a - b;
});

console.log(numbers);
```

Output:

```text
[10, 20, 30, 40]
```

Here, `a - b` sorts the numbers in ascending order.

For descending order:

```js
let numbers = [40, 10, 30, 20];

numbers.sort(function (a, b) {
  return b - a;
});

console.log(numbers);
```

Output:

```text
[40, 30, 20, 10]
```

## d. Pattern recognition in problems

Pattern recognition means identifying a common type of logic or approach in a problem.

For example, if a problem asks to find whether a particular value exists in an array, we can recognize it as a **searching problem**.

If a problem asks to find only values that satisfy a condition, we can use a **filtering pattern**.

If a problem asks to calculate the total of all elements, we can use an **accumulation/reduction pattern**.

Some common patterns are:

```text
Searching       → Check elements one by one
Filtering       → Select elements based on a condition
Transformation  → Change each element
Accumulation    → Combine values into one result
Traversal       → Go through each element
```

Recognizing these patterns helps us choose the appropriate method or logic for solving a problem.

## e. Writing step-by-step logic clearly

Before writing code, a problem can be divided into smaller steps. This makes it easier to understand and solve.

For example, to find the largest number in an array:

```text
1. Start with the first element as the largest.
2. Go through the remaining elements one by one.
3. Compare each element with the current largest value.
4. If the current element is larger, update the largest value.
5. Continue until all elements are checked.
6. Return or display the largest value.
```

The same logic can then be converted into code:

```js
let numbers = [10, 25, 15, 40, 20];

let largest = numbers[0];

for (let i = 1; i < numbers.length; i++) {
  if (numbers[i] > largest) {
    largest = numbers[i];
  }
}

console.log(largest);
```

Output:

```text
40
```

Writing the logic step by step before coding (writing pseudocodes) helps break a large problem into smaller and easier parts.
