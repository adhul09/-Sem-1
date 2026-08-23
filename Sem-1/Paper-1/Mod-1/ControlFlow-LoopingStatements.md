## Understand Control Flow - Looping Statements

## a. for, while, do-while

**for:**

Used to repeat a block of code a specific number of times.

Eg:

```js
for (let i = 1; i <= 5; i++) {
  console.log(i);
}
```

**while:**

Used to repeat a block of code as long as the condition is true.

Eg:

```js
let i = 1;

while (i <= 5) {
  console.log(i);
  i++;
}
```

**do-while:**

Similar to `while`, but the code runs at least once before checking the condition.

Eg:

```js
let i = 1;

do {
  console.log(i);
  i++;
} while (i <= 5);
```

## b. for...of and for...in

**for...of:**

Used to loop through the values of an iterable such as an array or string.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];

for (let fruit of fruits) {
  console.log(fruit);
}
```

**for...in:**

Used to loop through the keys or properties of an object.

Eg:

```js
let student = {
  name: "Adhul",
  age: 18
};

for (let key in student) {
  console.log(key);
}
```

## c. break and continue

**break:**

Used to stop the loop completely.

Eg:

```js
for (let i = 1; i <= 5; i++) {
  if (i == 3) {
    break;
  }

  console.log(i); // 1  2 
}
```

**continue:**

Used to skip the current iteration and continue with the next iteration.

Eg:

```js
for (let i = 1; i <= 5; i++) {
  if (i === 3) {
    continue;
  }

  console.log(i); // 1  2  4  5 
}
```

## d. Nested loops

A loop placed inside another loop is called a nested loop.  
Eg:

```js
for (let i = 1; i <= 2; i++) {
  for (let j = 1; j <= 3; j++) {
    console.log(i, j);
  }
}
```
Here, the inner loop runs completely for each iteration of the outer loop.
