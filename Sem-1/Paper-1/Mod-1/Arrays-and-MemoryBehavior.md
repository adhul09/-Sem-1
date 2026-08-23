# Understanding Arrays and Memory Behavior

## a. What is an array?

An array is a data structure used to store multiple values in a single variable.

The values in an array are stored in an ordered manner and each value has an index.

An array can store different types of values, but usually we store values of the same type.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];
```

Here, `fruits` is an array containing three values.

## b. Declaring and initializing arrays

An array can be created using square brackets `[]`.

Eg:

```js
let numbers = [10, 20, 30, 40];
```

An empty array can also be created and values can be added later.

Eg:

```js
let numbers = [];

numbers[0] = 10;
numbers[1] = 20;
numbers[2] = 30;
```

Arrays can also contain different types of values.

Eg:

```js
let data = ["John", 20, true];
```

## c. Indexing and accessing elements

Array indexing starts from `0`, not `1`.

Eg:

```js
let fruits = ["Apple", "Banana", "Mango"];
```

The indexes are:

```text
Apple  → 0
Banana → 1
Mango  → 2
```

We can access an element using its index.

Eg:

```js
console.log(fruits[0]); // Apple
console.log(fruits[2]); // Mango
```


## d. Reference vs primitive behavior 

Primitive values such as `number`, `string`, and `boolean` are copied by value.

Eg:

```js
let a = 10;
let b = a;

b = 20;

console.log(a); // 10
console.log(b); // 20
```

Here, changing `b` does not affect `a`.

Arrays and objects behave differently because they are reference types.

When an array is assigned to another variable, both variables refer to the same array.

Eg:

```js
let arr1 = [10, 20, 30];

let arr2 = arr1;

arr2[0] = 100;

console.log(arr1); // [100, 20, 30]
console.log(arr2); // [100, 20, 30]
```

Here, changing `arr2` also changes `arr1` because both variables refer to the same array in memory.

So, the basic difference is:

* **Primitive values** -> copied by value
* **Arrays and objects** -> copied by reference
