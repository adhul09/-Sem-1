# Object-Oriented Programming (OOP)

OOP is a way of organizing code around **objects** — things that have properties (data) and methods (actions), similar to how we describe real-world things.

## a. Classes and Objects

A **class** is a blueprint. An **object** is a real instance created from that blueprint.

```js
class Car {
  constructor(brand, color) {
    this.brand = brand;
    this.color = color;
  }

  drive() {
    console.log(`${this.brand} is driving`);
  }
}

const myCar = new Car("Toyota", "Red"); // object created from class
myCar.drive(); // "Toyota is driving"
```

---

## b. Constructors

The `constructor` is a special method that runs automatically when a new object is created — it sets up the initial values.

```js
class Student {
  constructor(name, grade) {
    this.name = name;
    this.grade = grade;
  }
}

const s1 = new Student("Adhul", "A");
console.log(s1.name); // "Adhul"
```

Every time you write `new Student(...)`, the constructor runs with those values.

---

## c. Inheritance

Inheritance lets one class reuse and extend another class's features, using `extends`.

```js
class Animal {
  constructor(name) {
    this.name = name;
  }
  speak() {
    console.log(`${this.name} makes a sound`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks`);
  }
}

const dog = new Dog("Rex");
dog.speak(); // "Rex barks"
```
`Dog` inherits from `Animal`, but overrides the `speak()` method with its own version.

Use `super()` to call the parent class's constructor:
```js
class Dog extends Animal {
  constructor(name, breed) {
    super(name);       // runs Animal's constructor
    this.breed = breed;
  }
}
```

---

## d. Encapsulation and Polymorphism

**Encapsulation** — keeping data protected inside a class, only exposing what's needed. In JS, this is often done with `#` for private fields.

```js
class BankAccount {
  #balance = 0; // private, can't be accessed directly outside

  deposit(amount) {
    this.#balance += amount;
  }
  getBalance() {
    return this.#balance;
  }
}

const acc = new BankAccount();
acc.deposit(100);
console.log(acc.getBalance()); // 100
console.log(acc.#balance);     // ❌ Error — private
```

**Polymorphism** — different classes can have a method with the same name, but each behaves differently (like the `speak()` example above — `Dog` and `Animal` both have `speak()`, but they do different things).

---

## e. Organizing Code Using OOP Concepts

Instead of scattering related data and functions everywhere, OOP groups them logically:

```js
class Product {
  constructor(name, price) {
    this.name = name;
    this.price = price;
  }
  applyDiscount(percent) {
    this.price -= this.price * (percent / 100);
  }
}

const item = new Product("Shoes", 1000);
item.applyDiscount(10);
console.log(item.price); // 900
```

This keeps everything about a "Product" — its data and its behavior — together in one place, making the code easier to read, reuse, and maintain as projects grow.