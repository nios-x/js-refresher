# JavaScript Learning Guide

Welcome to this JavaScript reference guide. It covers the most important language concepts, examples, and best practices for beginners and intermediate learners.

---

## 1. What is JavaScript?

JavaScript is a high-level, interpreted programming language used primarily for web development. It is:

- dynamic and loosely typed
- single-threaded with asynchronous capabilities
- executed by browsers on the client and by servers using environments like Node.js
- used to build interactive webpages, server APIs, desktop apps, and more

---

## 2. Running JavaScript

### Browser
JavaScript can run directly in the browser console or in a `<script>` tag inside HTML.

### Node.js
Install Node.js and run scripts using:

```bash
node index.js
```

---

## 3. Syntax and Comments

```js
// Single-line comment
/*
  Multi-line comment
*/
```

### Statements and Semicolons
Semicolons are optional in many cases, but using them consistently avoids errors.

---

## 4. Variables

### `var`

- function-scoped or global-scoped
- can be redeclared and reassigned

```js
var x = 10;
if (true) {
  var x = 20;
  console.log(x); // 20
}
console.log(x); // 20
```

### `let`

- block-scoped
- can be reassigned but not redeclared in the same scope

```js
let y = 10;
if (true) {
  let y = 20;
  console.log(y); // 20
}
console.log(y); // 10
```

### `const`

- block-scoped
- cannot be reassigned
- objects and arrays declared with `const` can still be mutated

```js
const z = 10;
// z = 20; // Error
const arr = [1, 2];
arr.push(3);
console.log(arr); // [1, 2, 3]
```

---

## 5. Data Types

### Primitive Types

- `Number` - integers and floating point values
- `String` - text
- `Boolean` - `true` or `false`
- `Null` - explicit absence of value
- `Undefined` - variable declared but not initialized
- `Symbol` - unique identifier
- `BigInt` - very large integers

```js
let n = 42;
let name = "Alice";
let active = true;
let emptyValue = null;
let notDefined;
let id = Symbol("id");
let big = 9007199254740991n;
```

### Non-Primitive Types

- `Object`
- `Array`
- `Function`

```js
const person = {
  name: "Amit",
  age: 25,
};
const colors = ["red", "green", "blue"];
function greet() {
  console.log("Hello!");
}
```

---

## 6. Operators

### Arithmetic
`+`, `-`, `*`, `/`, `%`, `**`

```js
console.log(5 + 3); // 8
console.log(2 ** 3); // 8
```

### Assignment
`=`, `+=`, `-=`, `*=`, `/=`

### Comparison
`===`, `!==`, `==`, `!=`, `>`, `<`, `>=`, `<=`

Use `===` and `!==` for strict comparison to avoid type coercion.

### Logical
`&&`, `||`, `!`

### String Concatenation

```js
console.log("Hello" + " " + "World");
```

### Common pitfalls

```js
console.log(null === undefined); // false
console.log(5 > 3 > 2); // false
console.log([] === []); // false
console.log("10" > "9"); // false
console.log(NaN === NaN); // false
console.log(true == 1); // true
console.log(undefined > 0); // false
```

---

## 7. Control Flow

### Conditionals

```js
if (score >= 90) {
  console.log("A");
} else if (score >= 80) {
  console.log("B");
} else {
  console.log("C");
}
```

### Switch

```js
switch (color) {
  case "red":
    console.log("Stop");
    break;
  case "green":
    console.log("Go");
    break;
  default:
    console.log("Wait");
}
```

### Loops

```js
for (let i = 0; i < 5; i++) {
  console.log(i);
}

let i = 0;
while (i < 5) {
  console.log(i);
  i++;
}
```

---

## 8. Functions

### Function Declaration

```js
function sum(a, b) {
  return a + b;
}
```

### Function Expression

```js
const multiply = function(a, b) {
  return a * b;
};
```

### Arrow Function

```js
const divide = (a, b) => a / b;
```

### Default Parameters

```js
function greet(name = "Guest") {
  console.log(`Hello, ${name}!`);
}
```

### Rest and Spread

```js
function add(...numbers) {
  return numbers.reduce((sum, n) => sum + n, 0);
}
const nums = [1, 2, 3];
console.log(add(...nums));
```

---

## 9. Objects

### Object Literals

```js
const user = {
  name: "Riya",
  age: 28,
  sayHello() {
    console.log(`Hello, ${this.name}`);
  },
};
```

### Accessing Properties

```js
console.log(user.name);
console.log(user["age"]);
```

### Adding and Removing Properties

```js
user.city = "Delhi";
delete user.age;
```

### `this` Keyword

- In object methods, `this` refers to the object.
- In standalone functions, `this` is `undefined` in strict mode.

---

## 10. Arrays

```js
const arr = [10, 20, 30];
console.log(arr.length);
console.log(arr[0]);
```

### Common Methods

- `push()`, `pop()`
- `shift()`, `unshift()`
- `map()`, `filter()`, `reduce()`
- `find()`, `includes()`, `slice()`, `splice()`

```js
const doubled = arr.map(x => x * 2);
const filtered = arr.filter(x => x > 15);
```

---

## 11. Scope and Hoisting

### Scope

- global scope
- function scope
- block scope (`let`, `const`)

### Hoisting

- `var` declarations are hoisted and initialized with `undefined`
- `let` and `const` are hoisted in the temporal dead zone and cannot be used before declaration
- function declarations are hoisted completely

```js
console.log(a); // undefined
var a = 5;
```

---

## 12. Closures

A closure is a function that remembers the environment in which it was created.

```js
function outer() {
  let outerVar = "I'm in the outer scope!";
  function inner() {
    console.log(outerVar);
    outerVar = "Updated";
  }
  return inner;
}
const closure = outer();
closure();
closure();
```

Closures are useful for creating private variables and function factories.

---

## 13. ES6+ Features

### Template Literals

```js
const name = "Sara";
console.log(`Hello, ${name}!`);
```

### Destructuring

```js
const point = { x: 10, y: 5 };
const { x, y } = point;
const nums = [1, 2, 3];
const [first, second] = nums;
```

### Modules

```js
// export.js
export const value = 42;

// import.js
import { value } from './export.js';
```

### Classes

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  greet() {
    console.log(`Hello, ${this.name}`);
  }
}
```

---

## 14. Asynchronous JavaScript

### Callbacks

```js
setTimeout(() => {
  console.log("Hello after 1 second");
}, 1000);
```

### Promises

```js
const promise = new Promise((resolve, reject) => {
  setTimeout(() => resolve("Done"), 500);
});
promise.then(value => console.log(value));
```

### `async` / `await`

```js
async function fetchData() {
  const response = await fetch("https://api.example.com/data");
  const data = await response.json();
  console.log(data);
}
```

---

## 15. Useful Tips

- Prefer `const` for values that should not be reassigned.
- Use `===` instead of `==` unless type coercion is intentional.
- Keep functions small and focused.
- Use array methods instead of manual loops when appropriate.
- Avoid mutating objects and arrays when possible.

---

## 16. Learning Path

1. Syntax, variables, and data types
2. Conditionals and loops
3. Functions and arrays
4. Objects and object methods
5. Scope, hoisting, and closures
6. ES6+ features
7. Asynchronous JavaScript and promises
8. DOM manipulation and browser APIs

---

## 17. Further Reading

- MDN Web Docs: https://developer.mozilla.org/en-US/docs/Web/JavaScript
- JavaScript.info: https://javascript.info/
- Node.js documentation: https://nodejs.org/en/docs/

---

## 18. Example Exercises

- Write a function to reverse a string.
- Create a function that filters out even numbers from an array.
- Build an object representing a book and add a method to print the title.
- Create a promise that resolves after 2 seconds.

---

## 19. Quick Reference

```js
const x = 5;
let y = "Hello";
const obj = { a: 1 };
const arr = [1, 2, 3];
function add(a, b) {
  return a + b;
}
```

This README is now a complete guide to help you study JavaScript step-by-step.
