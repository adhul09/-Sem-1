# Understanding Objects and Basic Data Structuring

## a. Creating and accessing objects

An object is a data structure used to store related data in the form of key-value pairs.

An object can be created using curly braces `{}`.

Eg:

```js
let person = {
  name: "John",
  age: 20,
  city: "Kochi"
};
```

The values of an object can be accessed using the key.

### Dot notation

```js
console.log(person.name); // John
console.log(person.age);  // 20
```

### Bracket notation

```js
console.log(person["name"]); // John
console.log(person["age"]);  // 20
```

Bracket notation is useful when the key is stored in a variable.

Eg:

```js
let key = "name";

console.log(person[key]); // John
```

We can also change the value of an existing property.

Eg:

```js
person.age = 21;

console.log(person.age); // 21
```

## b. Key-value structure

Objects store data using **key-value pairs**.

Eg:

```js
let student = {
  name: "Alex",  // string 
  age: 21,       // number
  course: "MERN" // string
};
```

Here:

```text
name   -> "Alex"
age    -> 21
course -> "MERN"
```

The left side is the **key** and the right side is the **value**.

Keys are used to identify and access the corresponding values.

An object can contain different types of values.


## c. Nested objects and arrays

An object can contain another object or an array as a value. This is called nesting.

### Nested object

Eg:

```js
let student = {
  name: "Alex",
  address: {
    city: "Kochi",
    state: "Kerala"
  }
};
```

The nested object's values can be accessed using multiple dot operators.

```js
console.log(student.address.city); // Kochi
console.log(student.address.state); // Kerala
```

### Array inside an object

An object can also contain an array.

Eg:

```js
let student = {
  name: "Alex",
  subjects: ["JavaScript", "React", "Node"]
};

console.log(student.subjects[0]); // JavaScript
console.log(student.subjects[1]); // React
```

### Array of objects

An array can also contain multiple objects.

Eg:

```js
let students = [
  {
    name: "Alex",
    age: 20
  },
  {
    name: "John",
    age: 22
  }
];

console.log(students[0].name); // Alex
console.log(students[1].age);  // 22
```

## d. Representing real-world data using objects

Objects are useful for representing real-world entities and their properties.

Eg:

```js
let user = {
  name: "Alex",
  email: "alex@example.com",
  age: 21,
  skills: ["JavaScript", "React", "Node.js"]
};
```

Objects make it easier to organize related information together and are widely used to represent data in JavaScript and web applications.
