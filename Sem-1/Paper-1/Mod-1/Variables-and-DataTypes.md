# Understand Variables and Data Types

## a. Variables 

**var:**
- Function-scoped (leaks outside if/for  blocks, may cause bugs)
- Can be redeclared and updated
- Is initialized as undefined when hoisted 

**let:**
- Block-scoped 
- Can be updated, but not redeclared in the same scope
- Not initialized when hoisted 

**const:**
- Block-scoped
- Cannot be updated or redeclared



## b. Primitive data types:

**i. string**  
Text, wrapped in quotes   
Eg:
```js 
let name = "Adhul";
```
**ii. number**  
All numbers    
Eg:
```js
let age = 18;
let mark = 3.33;
```
**iii. boolean**  
True or False  
Eg:
```js
let ch = true ;
```
**iv. null**  
Represents absence of value  
Eg: 
```js
let x = null ;
```
**v. undefined**  
Represents a variable thats been declared but not yet assigned a value 
Eg:  
```js
let y ;
console.log(y) // returns undefined
```

## c. Arrays and objects

- Arrays - an ordered list of values, accessed by index (starting at 0)  
Eg: 
```js
let num = [1, 2, 3];
```
- Objects — a collection of key-value pairs, accessed by key name  
Eg:
```js
let stud = {
  name: "Adhul",
  age: 18
  };
```

## d. Type conversion and coercion

- Type Conversion (explicit conversion) — you deliberately convert a type using a function  
Eg:
```js 
let x = "9";       //9 (type -> String)
num1 = Number(x);  //9 (type -> Number)
```
- Type Coercion (implicit conversion) — JavaScript itself automatically converts type based on the operaion its assigned  
Eg:
```js
console.log("9" + 0)  //90 (type -> String)
```

