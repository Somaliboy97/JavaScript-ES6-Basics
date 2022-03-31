# JavaScript ES6 Basics

*Click <img src="assets/star.png" width="18" height="18" align="absmiddle" title="Star" /> if you like the project. Pull Request are highly appreciated.*

<br/>

## Related Interview Questions

* [JavaScript Interview Questions](https://github.com/learning-zone/javascript-interview-questions/blob/master/README.md)
* [JavaScript Design Patterns](https://github.com/learning-zone/JavaScript-Design-Patterns/blob/main/README.md)
* [JavaScript Coding Practice](https://github.com/learning-zone/JavaScript-Coding-Practice/blob/main/README.md)

<br/>

## Table of Contents

* [Introduction](#-1-introduction)
* ES6 New Features
    * [let](#-21-let)
    * [let vs var](#-22-let-vs-var)
    * [const](#-23-const)
    * [Arrow Function](#-24-arrow-function)
    * [Default Function Parameters](#-25-default-function-parameters)
    * [Rest Parameter](#-26-rest-parameter)
    * [Spread Operator](#-27-spread-operator)
    * [for…of](#-28-forof)
    * [Binary and Octal literals](#-29-binary-and-octal-literals)
    * [Template literals](#-210-template-literals)
    * [Enhanced Object literals](#-211-Enhanced-object-literals)
* Destructuring
    * [Array Destructuring](#-31-array-destructuring)
    * [Object Destructuring](#-32-object-destructuring)
* ES6 Modules
    * [ES6 modules](#-4-es6-modules)
* ES6 Classes
    * [Classes](#-51-classes)
    * [Getters and Setters](#-52-getters-and-setters)
    * [Class Expression](#-53-class-expression)
    * [Static methods](#-54-static-methods)
    * [Static Properties](#-55-static-properties)
    * [Computed property](#-56-computed-property)
    * [Inheritance](#-57-inheritance)
    * [new.target](#-58-newtarget)
* Symbol
    * [Symbol](#-6-symbols)
* Iterators & Generators
    * [Iterators](#-71-iterators)
    * [Generators](#-72-generators)
    * [yield](#-73-yield)
* Promises
    * [Promises](#-81-promises)
    * [Promise chaining](#-82-promise-chaining)
    * [Promise composition](#-83-promise-composition)
    * [Promise error handling](#-84-promise-error-handling)
* ES6 Collections
    * [Set](#-91-set)
    * [Weakset](#-92-weakset)
    * [Map](#-93-map)
    * [Weakmap](#-94-weakmap)
* Array Extensions
    * [Array.of()]()
    * [Array.from()]()
    * [Array find()](#-array-find-methods)
    * [Array findIndex()]()
* Object Extensions
    * [Object.assign()]()
    * [Object.is()]()
* String Extensions
    * [String startsWith()]()
    * [String endsWith()]()
    * [String includes()]()
* Proxy & Reflection
    * [Proxy](#-proxies)
    * [Reflection](#-reflect)
* Miscellaneous Features
    * [Unicode](#-unicode)
    * [Proper Tail calls](#-proper-tail-calls)

<br/>

## # 1. Introduction

JavaScript ES6 (also known as ECMAScript 2015 or ECMAScript 6) is the newer version of JavaScript that was introduced in 2015.

ECMAScript is the standard that JavaScript programming language uses. ECMAScript provides the specification on how JavaScript programming language should work.

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.1. let

ES6 provides a new way of declaring a variable by using the `let` keyword. The `let` keyword is similar to the `var` keyword, except that these variables are **blocked-scope**.

**Syntax:**

```js
let variable_name;
```

In JavaScript, blocks are denoted by curly braces `{}` , for example, the `if else`, `for`, `do while`, `while`, `try catch` and so on.

**Example:**

```js
let x = 10;
if (x === 10) {
  let x = 20;
  console.log(x); // 20:  reference x inside the block
}
console.log(x); // 10: reference at the begining of the script

// Output:
20
10
```

Because the `let` keyword declares a block-scoped variable, the `x` variable inside the `if` block is a **new variable** and it shadows the `x` variable declared at the top of the script. Therefore, the value of `x` in the console is 20.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-let-zikqqb?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.2. let vs var

The `var` variables belong to the global scope when you define them outside a function. When you declare a variable inside a function using the `var` keyword, the scope of the variable is local. For example:

```js
function increase() {
    var counter = 10;
}
// cannot access the counter variable here
```

Here, the counter variable is local to the increase() function. It cannot be accessible outside of the function.

The following example displays four numbers from 0 to 4 inside the loop and the number 5 outside the loop.

```js
for (var i = 0; i < 3; i++) {
  console.log("Inside the loop:", i);
}

console.log("Outside the loop:", i);

// Output:
Inside the loop: 0 
Inside the loop: 1 
Inside the loop: 2 
Outside the loop: 3
```

Here, the i variable is a global variable. Therefore, it can be accessed from both inside and after the for loop.

The following example uses the `let` keyword instead of the `var` keyword:

```js
for (let i = 0; i < 3; i++) {
  console.log("Inside the loop:", i);
}

console.log("Outside the loop:", i);

// Output
Inside the loop: 0
Inside the loop: 1
Inside the loop: 2

Uncaught ReferenceError: i is not defined
```

Here, the variable **i** is blocked scope. It means that the variable **i** only exists and can be accessible inside the for loop block.

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-let-vs-var-yvu11z)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.3. const

ES6 provides a new way of declaring a constant by using the `const` keyword. The `const` keyword creates a **read-only** reference to a value.

```js
const CONSTANT_NAME = value;
```

Like the `let` keyword, the `const` keyword declares **blocked-scope** variables. However, the **block-scoped** variables declared by the `const` keyword can\'t be **reassigned**.

```js
const RATE = 0.1;
RATE = 0.2; // TypeError
```

The const keyword ensures that the variable it creates is read-only. However, it doesn’t mean that the actual value to which the const variable reference is immutable. For example:

```js
const person = { age: 20 };
console.log(person.age); // 20

person.age = 30; // OK
console.log(person.age); // 30
```

Even though the person variable is a constant, you can change the value of its property.

However, you cannot reassign a different value to the person constant like this:

```js
person = { age: 40 }; // TypeError
```

If you want the value of the person object to be immutable, you have to freeze it by using the Object.freeze() method:

```js
const person = Object.freeze({age: 20});
person.age = 30; // TypeError
```

*Note: `Object.freeze()` is shallow, meaning that it can freeze the properties of the object, not the objects referenced by the properties.*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-const-prej6w)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.4. Arrow Function

The Arrow function provides a more concise syntax for writing function expressions by opting out the function and return keywords using fat arrow(`=>`) notation.

**Syntax:**

```js
let myFunction = (arg1, arg2, ...argN) => expression
```

```js
// Function Expression 
let add = function (x, y) {
  return x + y;
};
console.log(add(10, 20)); // 30
```

The above function can be written as

```js
// Arrow functions
let add = (x, y) => x + y;
console.log(add(10, 20)); // 30
```

**Example 01:** Arrow Function with No Argument

If a function doesn\'t take any argument, then you should use empty parentheses.

```js
let greet = () => console.log('Hello');
greet(); // Hello
```

**Example 02:** Arrow Function with One Argument

If a function has only one argument, you can omit the parentheses.

```js
let greet = x => console.log(x);
greet('Hello'); // Hello 
```

**Example 03:** Arrow Function as an Expression

You can also dynamically create a function and use it as an expression.

```js
let age = 25;

let welcome = (age < 18) ?
  () => console.log('Baby') :
  () => console.log('Adult');

welcome(); // Adult
```

**Example 04:** Multiline Arrow Functions

If a function body has multiple statements, you need to put them inside curly brackets `{}`.

```js
let area = (r) => {
  const pi = 3.14;
  return pi * r * r;
}

let result = area(10);
console.log(result); // 314
```

*Note: Unlike regular functions, arrow functions do not have their own `this`. The value of `this` inside an arrow function remains the same throughout the lifecycle of the function and is always bound to the value of `this` in the closest non-arrow parent function.*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-arrow-function-yl7oqo?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.5. Default Function Parameters

Default parameters allow named parameters of a function to be initialized with default values if no value or undefined is passed.

**Syntax:**

```js
function fn(param1=default1, param2=default2,..) {
  // ...
}
```

Prior to ES6, you need check for undefined values and provide the default value for undefined values using if/else or ternary operator

```js
function sum(a, b) {
  a = (typeof a !== 'undefined') ? a : 10;
  b = (typeof b !== 'undefined') ? b : 20;
  return a + b;
}

console.log(sum()); // 30
console.log(sum(20)); // 40
```

In ES6, these checks can be avoided using default parameters

```js
function sum(a = 10, b = 20) {
  return a + b;
}

console.log(sum()); // 30
console.log(sum(20)); // 40
console.log(sum(20, 30)); // 50
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-default-parameters-8uu0m8?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.6. Rest Parameter

The rest parameter is used to represent an indefinite number of arguments as an array. The important point here is only the function\'s last parameter can be a "rest parameter".

This feature has been introduced to reduce the boilerplate code that was induced by the arguments.

```js
function sum(...args) {
  return args.reduce((previous, current) => {
    return previous + current;
  });
}

console.log(sum(10)); // 10
console.log(sum(10, 20)); // 30
console.log(sum(10, 20, 30)); // 60
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-rest-parameters-w8zy28?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.7. Spread Operator

The spread operator allows you to spread out elements of an iterable object such as an **array**, **map**, or **set**.

**Example:**

```js
const odd = [1, 3, 5];
const combined = [2, 4, 6, ...odd];

console.log(combined); // [ 2, 4, 6, 1, 3, 5 ]
```

JavaScript spread operator and array manipulation

**1. Constructing array literal:**

The spread operator allows to insert another array into the initialized array when you construct an array using the literal form.

```js
let initialChars = ['A', 'B'];
let chars = [...initialChars, 'C', 'D'];

console.log(chars); // ["A", "B", "C", "D"]
```

**2. Concatenating arrays:**

```js
let numbers = [10, 20];
let moreNumbers = [30, 40];
let allNumbers = [...numbers, ...moreNumbers];

console.log(allNumbers); // [10, 20, 30, 40]
```

**3. Copying an array:**

```js
let scores = [80, 70, 90];
let copiedScores = [...scores];

console.log(copiedScores); // [80, 70, 90]
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-spread-operator-0jh98u)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.8. For..of

The `for...of` statement creates a loop iterating over **iterable objects**, including: built-in `String`, `Array`, array-like objects (e.g., `arguments` or `NodeList`), `TypedArray`, `Map`, `Set`, and user-defined iterables.

It invokes a custom iteration hook with statements to be executed for the value of each distinct property of the object.

**Syntax:**

```js
for (variable of iterable) {
   // ...
}
```

**Example 01:** Iterating over an Array

```js
const iterable = [10, 20, 30];

for (const value of iterable) {
  console.log(value);
}

// Output
10
20
30
```

**Example 02:** Iterating over a String

```js
const iterable = 'Hello';

for (const value of iterable) {
  console.log(value);
}

// Output
"H"
"e"
"l"
"l"
"o"
```

**Example 03:** Iterating over a Map

```js
const iterable = new Map([['A', 10], ['B', 20], ['C', 30]]);

for (const [key, value] of iterable) {
  console.log(key + " -> " + value);
}

// Output
A -> 10
B -> 20
C -> 30
```

**Example 04:** Iterating over a Set

```js
const iterable = new Set([10, 10, 20, 20, 30, 30]);

for (const value of iterable) {
  console.log(value);
}

// Output
10
20
30
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-for-of-ltt89x?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.9. Binary and Octal literals

ES5 provided numeric literals in octal (prefix 0), decimal (no prefix), and hexadecimal ( 0x) representation. ES6 added support for binary literals and improvements on octal literals.

**1. Binary literals:**

Prior to ES5, JavaScript didn\'t provide any literal form of binary numbers. So you need to use a binary string with the help of `parseInt()`

```js
const num = parseInt('111', 2);
console.log(num); // 7
```

Whereas ES6 added support for binary literals using the **0b** prefix followed by a sequence of binary numbers (i.e, 0 and 1).

```js
const num = 0b111;
console.log(num); // 7
```

**2. Octal literals:**

In ES5, to represent an octal literal, you use the zero prefix (0) followed by a sequence of octal digits (from 0 to 7).

```js
const num = 055;
console.log(num); // 45

// Note: Legacy octal literals are not allowed in strict mode
```

ES6 represents the octal literal by using the prefix **0o** followed by a sequence of octal digits from 0 through 7.

```js
let num = 0o10;
console.log(num); // 8
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-binary-literals-mllutq?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.10. Template literals

Template literals allows you to work with strings in a new way compared to ES5. These are just string literals allowing embedded expressions denoted by the dollar sign and curly braces (${expression}). These literals are enclosed by the backtick (` `) character instead of double or single quotes.

**Example:**

```js
let str = "World";
let message = `Hello ${str}`;

console.log(message); // Hello World
```

**Multiline Strings:**

```js
let msg = 'Multiline \n\
string';

console.log(msg);

// Multiline
// string
```

**Tagged Templates:**

A template tag carries the transformation on the template literal and returns the result string.

It can be used in creating components in `CSS-In-JS` styled components to use across the application

```js
function tag(strings) {
  console.log(strings.raw[0]); 
}

tag`Hello World`;

// Output
Hello World
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-template-literals-d005t4?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 2.11. Enhanced Object literals

The object literal is one of the most popular patterns for creating objects in JavaScript. Object literals are extended to support setting the prototype at construction, defining methods, making super calls, and computing property names with expressions

The important enhancements of object literals are,

**Property Shorthand:**

Object\'s properties are often created from variables with the same name.

Let\'s see the ES5 representation

```js
var a = 1, b = 2, c = 3;
var obj = {
    a: a,
    b: b,
    c: c
  };
console.log(obj);

// Output
{a: 1, b: 2, c: 3}
```

and it can be represented in a shorter syntax as below,

```js
let a = 1, b = 2, c = 3;
let obj = {
    a,
    b,
    c
  };
console.log(obj);

// Output
{a: 1, b: 2, c: 3}
```

**Method Shorthand:**

Prior to ES6, when defining a method for an object literal, you need to specify the name and full function definition

```js
let server = {
  name: "Server",
  restart: function () {
    console.log("The" + this.name + " is restarting...");
  }
};
server.restart();

// Output
The Server is restarting... 
```

This can be avoided in ES6,

```js
let server = {
  name: "Server",
  restart() {
    console.log("The " + this.name + " is restarting...");
  }
};
server.restart();

// Output
The Server is restarting... 
```

**Computed Property Names:**

In ES5, it wasn\'t possible to use a variable for a key name during object creation stage.

```js
var key = "three",
  obj = {
    one: 10,
    two: 20
  };
obj[key] = 30;
```

Object keys can be dynamically assigned in ES6 by placing an expression in square brackets([])

```js
const key = "three",
  computedObj = {
    one: 10,
    two: 20,
    [key]: 30
  };
console.log(computedObj.one);

// Output
10
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-object-literals-byphgz?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 3.1 Array Destructuring

ES6 provides a new feature called destructing assignment that allows you to destructure properties of an object or elements of an array into individual variables.

**Basic variable assignment:**

```js
const keys = ["one", "two", "three"];
const [red, yellow, green] = keys;

console.log(red); // one
console.log(yellow); // two
console.log(green); // three
```

**Assignment separate from declaration:**

```js
let a, b;

[a, b] = [10, 20];

console.log(a); // 10
console.log(b); // 20
```

**Array destructuring and Default values:**

```js
let x, y;

[x = 10, y = 20] = [30];

console.log(x); // 30
console.log(y); // 20
```

**Swapping variables:**

```js
let a = 10, 
    b = 20;

[a, b] = [b, a];

console.log(a); // 20
console.log(b); // 10
```

**Assigning the rest of an array to a variable:**

```js
const [a, ...b] = [1, 2, 3];

console.log(a); // 1
console.log(b); // [2, 3]
```

**Functions that return multiple values:**

```js
function calculate(a, b) {
  return [a + b, a - b, a * b];
}

let [sum, difference, multiplication] = calculate(20, 10);

console.log(sum, difference, multiplication); // 30, 10, 200
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-array-destructuring-0k5c35?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 3.2. Object Destructuring

ES6 introduces the object destructuring syntax that provides an alternative way to assign properties of an object to variables.

**Syntax:**

```js
let { property1: variable1, property2: variable2 } = object;
```

**Simple assignment:**

```js
const num = { x: 10, y: 20 };
const { x, y } = num;

console.log(x); // 10
console.log(y); // 20
```

**Basic Object destructuring assignment:**

```js
const employee = {
  eId: "12345",
  name: "Dushyant Meena",
  email: "dushyant.meena@email.com"
};
const { eId, name, email } = employee;

console.log(eId); // 12345
console.log(name); // Dushyant Meena
console.log(email); // dushyant.meena@email.com
```

**Object destructuring and default values:**

```js
const { q = 100, w = 200 } = { e: 500 };

console.log(q); // 500
console.log(w); // 200
```

**Assigning new variable names:**

```js
const number = { x: 100, y: 200 };
const { x: val1, y: val2 } = number;

console.log(val1); // 100
console.log(val2); // 200
```

**Assignment without declaration:**

```js
let firstName, lastName;
({ firstName, lastName } = { firstName: "Gauri", lastName: "Pratima" });

console.log(firstName); // Gauri
console.log(lastName); // Pratima
```

**Object destructuring and rest operator:**

```js
let { a, b, ...args } = { a: 10, b: 20, c: 30, d: 40, e: 50 };

console.log(a);
console.log(b);
console.log(args);

// Output
100
200
{ c: 30, d: 40, e: 50 }
```

**Assigning new variable names and providing default values simultaneously:**

```js
const { a: num1 = 100, b: num2 = 200 } = { a: 300 };

console.log(num1); //300
console.log(num2); //200
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-object-destructuring-ecncqm?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 4. ES6 modules

An ES6 module is a JavaScript file that executes in strict mode only. It means that any variables or functions declared in the module won\'t be added automatically to the global scope.

ES6 has provided the built-in support for modules. Everything inside a module is private by default. Public variables, functions and classes are exposed using `export` statement and import the same using `import` statement.

**Export Statement:**

There are two types of exports:

**1. Named Exports:**

You can export each element or a single export statement to export all the elements at once

```js
// module "my-module.js"
const PI = Math.PI;

function add(...args) {
  return args.reduce((num, tot) => tot + num);
}

function multiply(...args) {
  return args.reduce((num, tot) => tot * num);
}

// private function
function print(msg) {
  console.log(msg);
}

export { PI, add, multiply };
```

**2. Default Exports:**

If we want to export a single value, you could use a default export

```js
// module "my-module.js"
export default function add(...args) {
  return args.reduce((num, tot) => tot + num);
}
```

**Import Statement:**

The static import statement is used to import read only live bindings which are exported by another module.

There are many variations of import scenarios as below,

```js
// 1. Import an entire module's contents
import * as name from "my-module";

//2.Import a single export from a module
import { export1 } from "my-module";

//3.Import multiple exports from a module
import { export1 , export2 } from "my-module";

//4.Import default export from a module
import defaultExport from "my-module";

//5.Import an export with an alias
import { export1 as alias1 } from "my-module";
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.1. Classes

ES6 Classes formalize the common JavaScript pattern of simulating class-like inheritance hierarchies using functions and prototypes. It support prototype-based inheritance, constructors, super calls, instance and static methods.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  getName() {
    return this.name;
  }
}

let Object = new Person("Prasad Shashi");
let name = Object.getName();

console.log(name); // "Prasad Shashi"
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-class-70hkd7)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.2. Getters and Setters

The accessor properties are methods that get or set the value of an object. For that, we use these two keywords:

* `get` - to define a getter method to get the property value
* `set` - to define a setter method to set the property value

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  get name() {
    return this._name;
  }
  set name(newName) {
    newName = newName.trim();
    if (newName === "") {
      throw "The name cannot be empty";
    }
    this._name = newName;
  }
}

let Object = new Person("Mala Amar");
let name = Object.name;

console.log(name); // "Mala Amar"
```

*Note: These setter and getter allow you to use the properties directly (without using the parenthesis)*

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-getters-and-setters-ugb9jx?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.3. Class expressions

A class expression is another way to define a class. Class expressions can be named or unnamed. The name given to a named class expression is local to the class\'s body. However, it can be accessed via the name property.

```js
// Unnamed Class
let Person = class {
  constructor(name) {
    this.name = name;
  }
  getName() {
    return this.name;
  }
};

let Object = new Person("Anjali Durga");
let name = Object.getName();

console.log(name); // "Anjali Durga"
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-class-expressions-ofbg0i)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.4. Static methods

The static keyword defines a static method or property for a class, or a class static initialization block. Neither static methods nor static properties can be called on instances of the class. Instead, they\'re called on the class itself.

Static methods are often utility functions, such as functions to create or clone objects, whereas static properties are useful for caches, fixed-configuration, or any other data you don't need to be replicated across instances.

```js
class Person {
  constructor(name) {
    this.name = name;
  }
  
  // Static Method
  static staticMethod(gender) {
    let name = gender === "male" ? "Aryan Sarin" : "Manju Soni";
    return new Person(name);
  }
}

let anonymous = Person.staticMethod("male");
console.log(anonymous);

// Output
Person {name: "Aryan Sarin", constructor: Object}
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-static-methods-3tf3li?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.5. Static Properties

Like a static method, a static property is shared by all instances of a class. To define static property, you use the static keyword followed by the property name like this:

```js
class Item {
  constructor(name, quantity) {
    this.name = name;
    this.quantity = quantity;
    this.constructor.count++;
  }
  // Static Properties
  static count = 0;
  
  // Static Method
  static getCount() {
    return Item.count++;
  }
}

let pen = new Item("Pen", 5);
let notebook = new Item("notebook", 10);

console.log(Item.getCount()); // 2
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-static-properties-xc03d4)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.6. Computed property

ES6 "Computed Property" feature allows you to have an expression in brackets `[]` (a piece of code that results in a single value like a variable or function invocation) be computed as a property name on an object.

```js
let propName = "fullName";

class Person {
  constructor(firstName, lastName) {
    this.firstName = firstName;
    this.lastName = lastName;
  }
  get [propName]() {
    return `${this.firstName} ${this.lastName}`;
  }
}

let person = new Person("Sharma", "Peri");
console.log(person.fullName);

// Output
Sharma Peri
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-computed-property-ns52qr?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.7. Inheritance

To create a class inheritance, use the `extends` keyword. A class created with a class inheritance inherits all the methods from another class. The `super()` method in the constructor is used to access all parent’s properties and methods that are used by the derived class.

```js
// Parent Class
class Vehicle {
  constructor(name, type) {
    this.name = name;
    this.type = type;
  }

  getName() {
    return this.name;
  }

  getType() {
    return this.type;
  }
}
// Child Class
class Car extends Vehicle {
  constructor(name) {
    super(name, "car");
  }

  getName() {
    return "It is a car: " + super.getName();
  }
}
let car = new Car("Tesla");

console.log(car.getName()); // It is a car: Tesla
console.log(car.getType()); // car
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-inheritance-vposow)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # 5.8. new.target

The `new.target` pseudo-property lets you detect whether a function or constructor was called using the **new** operator. In constructors and functions invoked using the new operator, `new.target` returns a reference to the constructor or function. In normal function calls, `new.target` is undefined.

```js
class Person {
  constructor(name) {
    this.name = name;
    console.log(new.target.name);
  }
}

class Employee extends Person {
  constructor(name, title) {
    super(name);
    this.title = title;
  }
}

let person = new Person("Tara Mishra"); // Person
let employee = new Employee("Aditya Kala", "Programmer"); // Employee
```

**&#9885; [Try this example on CodeSandbox](https://codesandbox.io/s/es6-new-target-dzurzb?file=/src/index.js)**

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Generators

A generator is a function that can stop or suspend midway and then continue from where it stopped while maintaining the context(saved across re-entrances). It can be defined using a function keyword followed by an asterisk(i.e, function* ()).

This function returns an iterator object and this iterator\'s **next()** method returns an object with a value property containing the yielded value and a done property which indicates whether the generator has yielded its last value.

```js
function* myGenerator(i) {
  yield i + 10;
  yield i + 20;
  return i + 30;
}
const myGenObj = myGenerator(10);

console.log(myGenObj.next().value); // 20
console.log(myGenObj.next().value); // 30
console.log(myGenObj.next().value); // 40
```

**Note:** We can use `yield*` to delegate to another generator function

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Set

Set is a built-in object to store collections of unique values of any type.

```js
let mySet = new Set()

mySet.add(1);
mySet.add(2);
mySet.add(2);
mySet.add('some text here');
mySet.add({one: 1, two: 2 , three: 3});

console.log(mySet); // Set [ 1, 2, 'some text here', {one: 1, two: 2 , three: 3} ]
console.log(mySet.size) // 4
console.log(mySet.has(2)); // true
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Weakset

The Set is used to store any type of data such as primitives and object types. Whereas WeakSet is an object to store weakly held objects in a collection. (i.e, WeakSet is the collections of objects only). Here weak means,  If no other references to an object stored in the WeakSet exist, those objects can be garbage collected.

```js
let myUserSet = new WeakSet();

let john = { name: "John" };
let rocky = { name: "Rocky" };
let alex = { name: "Alex" };
let nick = { name: "Nick" };

myUserSet.add(john);
myUserSet.add(rocky);
myUserSet.add(john);
myUserSet.add(nick);

console.log(myUserSet.has(john)); // true
console.log(myUserSet.has(alex)); // false
console.log(myUserSet.delete(nick));
console.log(myUserSet.has(nick)); // false
john = null;
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Map

Map is a collection of elements where each element is stored as a Key, value pair. It can hold both objects and primitive values as either key or value and iterates its elements in insertion order.

Let\'s take a map with different types of primitives and objects as key-value pairs and various methods on it,

```js
 let typeMap = new Map();
 var keyObj = {'one': 1}

 typeMap.set('10', 'string');   // a string key
 typeMap.set(10, 'number');     // a numeric key
 typeMap.set(true, 'boolean'); // a boolean key
 typeMap.set(keyObj, 'object'); // an object key
 console.log(typeMap.get(10)   ); // number
 console.log(typeMap.get('10') ); // string
 console.log(typeMap.get(keyObj)) // object
 console.log(typeMap.get({'one': 1})) // undefined
 console.log(typeMap.size ); // 3
 
 for(let item of typeMap) {
    console.log(item);
 }

 for(let item in typeMap) {
    console.log(item);
 }
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Weakmap

WeakMap object is a collection of key/value pairs in which the keys are weakly referenced. For this object, the keys must be objects and the values can be arbitrary values.

Let\'s see various methods of weakmap with below example,

```js
var weakMap = new WeakMap();
var obj1  = {}
var obj2  = {}

weakMap.set(obj1, 1);
weakMap.set(obj2, 2);
weakMap.set({}, {"four": 4});

console.log(weakMap.get(obj2)); // 2
console.log(weakMap.has({})); // return false even though empty object exists as key. Because the keys have different references

delete obj2;
console.log(weakMap.get(obj2)); // 2

weakMap.delete(obj1)
console.log(weakMap.get(obj1)); //undefined
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Unicode

Prior to ES6, JavaScript strings are represented by 16-bit character encoding (UTF-16). Each character is represented by 16-bit sequence known as code unit. Since the character set is been expanded by Unicode, you will get unexpected results from UTF-16 encoded strings containing surrogate pairs(i.e, Since it is not sufficient to represent certain characters in just 16-bits, you need two 16-bit code units).

```js
let str = '𠮷';

console.log(str.length);             // 2
console.log(text.charAt(0));        // ""
console.log(text.charAt(1));        // ""
console.log(text.charCodeAt(0));    // 55362(1st code unit)
console.log(text.charCodeAt(1));    // 57271(2nd code unit)

console.log(/^.$/.test(str)); // false, because length is 2
console.log('\u20BB7'); // 7!(wrong value)
console.log(str === '\uD842\uDFB7'); // true
```

ECMAScript 6 added full support for UTF-16 within strings and regular expressions. It introduces new Unicode literal form in strings and new RegExp u mode to handle code points, as well as new APIs(codePointAt, fromCodePoint) to process strings.

```js
let str = '𠮷';

// new string form
console.log('\u{20BB7}'); // "𠮷"

// new RegExp u mode
console.log(new RegExp('\u{20BB7}', 'u'));
console.log(/^.$/u.test(str)); // true

//API methods
console.log(str.codePointAt(0)); // 134071
console.log(str.codePointAt(1)); // 57271

console.log(String.fromCodePoint(134071));  // "𠮷"
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Symbols

Symbol is a new peculiar primitive data type of JavaScript, along with other primitive types such as string, number, boolean, null and undefined. The new symbol is created just by calling the Symbol function. i.e, Every time you call the Symbol function, you’ll get a new and completely unique value. You can also pass a parameter to Symbol(), which is useful for debugging purpose only.

Even though equality checks on two symbols is always false, it will be true while comparing symbols with `.for` method due to global registry (i.e, Symbols.for('key') === Symbols.for('key'))

These symbols are useful to uniquely identify properties or unique constants,

```js
//1. Object properties
let id = Symbol("id");
let user = {
  name: "John",
  age: 40,
  [id]: 111
};

for (let key in user) {
console.log(key); // name, age without symbols
}

console.log(JSON.stringify(user)); // {"name":"John", "age": 40}
console.log(Object.keys(user)); // ["name", "age"]
console.log( "User Id: " + user[id] ); // Direct access by the symbol works

//2. Unique constants
const logLevels = {
  DEBUG: Symbol('debug'),
  INFO: Symbol('info'),
  WARN: Symbol('warn'),
  ERROR: Symbol('error'),
};

console.log(logLevels.DEBUG, 'debug message');
console.log(logLevels.INFO, 'info message');

//3. Equality Checks
console.log(Symbol('foo') === Symbol('foo'));  // false
console.log(Symbol.for('foo') === Symbol.for('foo'));  // true
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Proxies

The Proxy object is used to create a proxy for another object, which can intercept and redefine fundamental operations for that object such as property lookup, assignment, enumeration, function invocation etc. These are used in many libraries and some browser frameworks.

The proxy object is created with two parameters with below syntax,

```js
let proxy = new Proxy(target, handler)
```

1. **target:** Object on which you want to proxy
2. **handler:** An object that defines which operations will be intercepted and how to redefine them.

The property Lookup Behavior of a user proxied object will be as below,

```js
const target = {
  name: "John",
  age: 3
};
const handler = {
  get: function(target, prop) {
    return prop in target ?
        target[prop] :
        `${prop} does not exist`;
  }
};

const user = new Proxy(target, handler);

console.log(user.name); // John
console.log(user.age); // John
console.log(user.gender); // gender does not exist
```

These proxies also enforce value validations. Let\'s take an example with set handler,

```js
let ageValidator = {
  set: function(obj, prop, value) {
    if (prop === 'age') {
      if (!Number.isInteger(value)) {
        throw new TypeError('The age is not an integer');
      }
      if (value > 200) {
        throw new RangeError('Invalid age');
      }
    }
    obj[prop] = value; // The default behavior to store the value
    return true; // Indicate success
  }
};

const person = new Proxy({}, validator);

person.age = 30;
console.log(person.age); // 30
person.age = 'old';    // Throws an exception
person.age = 200;        // Throws an exception
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Promises

A promise is an object which represent the eventual completion or failure of an asynchronous operation.

It is in one of these states:

**pending:**  Represents initial state, neither fulfilled nor rejected.
**fulfilled:** Indicates that the operation is completed successfully.
**rejected:** Indicates that the operation is failed.

A promise is said to be settled if it is either fulfilled or rejected, but not pending. The instance methods `promise.then()`, `promise.catch()`, and `promise.finally()` are used to associate further action with a promise that becomes settled. And these methods also return a newly generated promise object, which can optionally be used for chaining.

The promise chaining structure would be as below,

```js
const promise = new Promise(function(resolve, reject) {
                setTimeout(() => resolve(1), 1000);
            });
promise.then(function(result) {
      console.log(result); // 1
      return result * 2;
    }).then(function(result) {
      console.log(result); // 2
      return result * 3;
    }).then(function(result) {
      console.log(result); // 6
      return result * 4;
    }).catch(function(error){
       console.log(error);
    });
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Reflect

Reflection is the ability of a code to inspect and manipulate variables, properties, and methods of objects at runtime. JavaScript already provides `Object.keys(), Object.getOwnPropertyDescriptor(), and Array.isArray()` methods as classic refection features. In ES6, it has been officially provided through Reflect object. Reflect is a new global object which is used to call methods, construct objects, get and set properties, manipulate and extend properties.

Unlike most global objects, Reflect is not a constructor. i.e, You cannot use Reflect with the new operator or invoke the Reflect as a function. It is similar to Math and JSON objects in which all the methods of this object are static.

Let\'s see the usage of Reflect API with below examples,

1. **Creating objects using Reflect.construct();**

The `construct()` method behaves like the regular new operator, but as a function. It is equivalent to calling new target(...args) with an option to specify a different prototype. The syntax looks like as below,

```js
Reflect.construct(target, args [, newTarget]);
```

The method has below parameters,

1. target: The target function to call.
2. argumentsList: An array-like object specifying the arguments with which target should be called.
3. newTarget: The constructor whose prototype should be used. This is an optional parameter. i.e, If newTarget is not present, its value defaults to target.

**Example:**
```js
class User {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    }
};
let args = ['John', 'Emma'];
let john = Reflect.construct(
    User,
    args
);
console.log(john instanceof User);
console.log(john.fullName); // John Doe
```

2. **Calling a function using Reflect.apply():**

Prior to ES6, you can invoke a function with a specified `this` value and arguments by using the `Function.prototype.apply()` method.

For example, you can call `max()` static method of Math object,

```js
const max = Function.prototype.apply.call(Math.max, Math, [100, 200, 300]);
console.log(max);
```

In ES6, Reflect.apply() provides the same features as Function.prototype.apply() but in a less verbose syntax.

```js
const max = Reflect.apply(Math.max, Math, [100, 200, 300]);
console.log(max);
```

3. **Defining a property using Reflect.defineProperty():**

The `Reflect.defineProperty()` method is similar to `Object.defineProperty()` but it returns a Boolean value indicating whether or not the property was defined successfully instead of throwing an exception.

The syntax of this method looks like below,

```js
Reflect.defineProperty(target, propertyName, propertyDescriptor)
```

Let\'s define the age property on user object,

```js
class User {
    constructor(firstName, lastName) {
        this.firstName = firstName;
        this.lastName = lastName;
    }
    get fullName() {
        return `${this.firstName} ${this.lastName}`;
    }
};
let john = new User('John', 'Resig');
if (Reflect.defineProperty(john, 'age', {
        writable: true,
        configurable: true,
        enumerable: false,
        value: 33,
    })) {
    console.log(john.age);
} else {
    console.log('Cannot define the age property on the user object.');
}
```

4. **Delete property using Reflect.deleteProperty():**

The `Reflect.deleteProperty()` method is used to delete properties like the delete operator but as a function. It returns Boolean value indicating whether or not the property was successfully deleted.

```js
const user = {
  name: 'John',
  age: 33
};
console.log(Reflect.deleteProperty(user, 'age')); // true
console.log(user.age); // undefined
```

5. **Get property of an object using Reflect.get():**

The `Reflect.get` method is used to get a property on an object like the property accessor syntax but as a function.

```js
const user = {
  name: 'John',
  age: 33
};
console.log(Reflect.get(user, 'age')); // 33
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Proper Tail Calls

**Proper tail call(PTC)** is a technique where the program or code will not create additional stack frames for a recursion when the function call is a tail call.

For example, the below classic or head recursion of factorial function relies on stack for each step. Each step need to be processed upto `n * factorial(n - 1)`

```js
  function factorial(n) {
    if (n === 0) {
      return 1
    }
    return n * factorial(n - 1)
  }
  console.log(factorial(5)); //120
```

But if you use Tail recursion functions, they keep passing all the necessary data it needs down the recursion without relying on the stack.

```js
  function factorial(n, acc = 1) {
    if (n === 0) {
      return acc
    }
    return factorial(n - 1, n * acc)
  }
  console.log(factorial(5)); //120
```

The above pattern returns the same output as first one. But the accumulator keeps track of total as an argument without using stack memory on recursive calls.

The browsers which supports PTC do not generate stack overflow instead shows Infinity with below inputs,

```js
 console.log(factorial(10));
 console.log(factorial(100));
 console.log(factorial(1000));
 console.log(factorial(10000));
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>

## # Array find methods

ES6 introduced few array methods and two of them are `Array.find()` and `Array.findIndex()`.

**Array.find():**

This method returns the value of the first element in an array that satisfies the given test. Let\'s take an example of array with all even elements except one element and use `find` method to find the odd element.

```js
let arr = [2, 4, 5, 6, 8, 10];
function isOdd(i) {
  return i % 2 !== 0;
}
console.log(arr.find(isOdd)); // 5
```

**Array.findIndex():**

This method returns the index of the first element in the array that satisfies the given test. Let\'s take an example of array with all even elements except one element and use `findIndex` method to find the index of odd element.

```js
let arr = [2, 4, 5, 6, 8, 10];

function isOdd(i) {
  return i % 2 !== 0;
}
console.log(arr.findIndex(isOdd)); //2
```

<div align="right">
  <b><a href="#">↥ back to top</a></b>
</div>
