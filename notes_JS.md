# JavaScript notes

Here I will be retaking the notes I have taken during my Complete JavaScript course for documentation and rehearsal.

## Instance methods

Instance methods will be added to the prototype property, so all instances can use them.

## Static methods

Static methods are not added to the prototype property, thus they are not available for the instances (of classes for example)

Example:

```javascript
class PersonCl {
  constructor(fullName, birthYear) {
    this.fullName = fullName;
    this.birthYear = birthYear;
  }

  // Instance method
  calcAge() {
    // function
    console.log(2022 - this.birthYear);
  }

  // Static method
  static hey() {
    console.log("Hey there!");
    console.log(this);
  }
}

const jessica = new PersonCl("Jessica Davis", 1999);

jessica.calcAge();
PersonCl.hey();
```

## Encapsulation in JavasCript (not yet official)

Encapsulation is currently being developed in JavaScript is at stage 3/4.

There are:

- Public fields (instances): declared at the beginning of the class without a _const_ or _let_
- Private fields: marked with a **#**. Unreachable from outside of the class.
- Public methods: general methods as we use them daily.
- Private methods: marked with a **#**. Is not implemented yet.

## Working with classes overview

All objects created through class are called instances of that class. The instance IS an object, while the class is not.

### Important definitions:

**Abstraction:** Ignoring or hiding details that don't matter, allowing us to get an overview perspective of the thing we are implementing, instead of messing with details that don't really matter to our implementation.

**Encapsulation:** Keeping properties and methods private inside the class so they are inaccessible from outside the class. Some methods can be exposed as a public interface (API).

**Inheritance:** Making all properties and methods of a certain class available to a child class, forming a hierarchical relationship between classes. This allows us to reuse common logic and model real-world relationships.

**Polymorphism:** A child class can overwrite a method it inherited from a parent class.

In classical OOP objects (instances) are **instantiated** from classes which act as a blueprint. In JavaScript all objects are linked to a prototype object. The prototype object contains all methods and properites that all the linked objects can access and use. This is **prototypal inheritance.**

### There are three ways to create prototypes in JavaScript:

1. #### Constructor functions:

   Basic technique for creating objects from functions. In the following example _Car_ is a **constructor function**, which has a prototype property (_Car.prototype_). This is an **object**, inside which we have the _accelerate_ and the _brake_ methods. _Car.prototype_ has a reference back to _Car_ (_.constructor_)

   When we use the _new_ keyword a new, empty object is created. Then the _this_ keyword is set to the newly created object. An object's .**proto** will point to its constructor(miata.**proto** will point to _Car.prototype_). This way a **prototype chain** is formed.
   Example:

   ```javascript
   const Car = function (make, speed) {
     // Car constructor function is created
     this.make = make;
     this.speed = speed;
   };

   Car.prototype.accelerate = function () {
     // accelerate function is added to Car constructor function
     console.log((this.speed += 10));
   };

   Car.prototype.brake = function (decelaration = 10) {
     // brake function is added to Car constructor function
     console.log(this.speed - decelaration);
   };

   const miata = new Car("Miata", 230);
   miata.accelerate();
   miata.brake();
   ```

2. #### Classes:

   Classes in JavaScript are just sugarcoated constructor functions. The syntax is different, but the core methodology is the same. Classes are basically functions, and first of all a constructor method is needed to be added. It must be named constructor.

   Important:

   - Classes are NOT hoisted.
   - Classes are first-class citizens.
   - Classes are executed in strict mode.

   Example:

   ```javascript
   class CarCL {
     constructor(make, speed) {
       // Constructor sets the base values
       this.make = make;
       this.speed = speed;
     }

     accelerate() {
       // accelerate function is defined and available for instances of CarCL
       console.log((this.speed += 10));
     }

     brake() {
       // brake function is defined and available for instances of CarCL
       console.log((this.speed -= 10));
     }
   }
   ```

## Inheritance with JavaScript classes (constructor functions)

## Get & Set

# Asynchronous and synchronous JavaScript, APIs

## Synchronous

- Most code is **synchronous**
- Sync code is executed **line by line**
- Each line of code **waits** for the previous to finish
- Long running operations **block** code execution

## Asynchronous

- Async code is executed **after a task that runs in the "background" finishes**
- Async code is **non-blocking**
- Callback functions and EventListeners alone do **NOT** make code async

## AJAX

**A**synchronous **J**avaScript **A**nd **X**ML
Allows us to communicate with remote web servers in an async way. With AJAX calls we can request data from web serververs dynamically.
_Fun-fact: XML data format is no longer used for data transmitting on the web, JSON is used instead._

## API

**A**pplication **P**rogramming **I**nterface: Piece of software that can be used by another software in order to allow applications to talk to each other.

### Online API

Application running on a server, that receives requests for data, and sends data back as a response.

### CORS

**C**ross **O**rigin **R**esource **S**haring. Without it we cannot access a 3rd party API from our code.

The modell of client and server communications through APIs is called the R**equest-response model** or **Client-server architecture**.

## Promises

A **promise** is an object that is used as a placeholder for the future result of an asynchronous operation.

- With promises we no longer need to rely on events and callbacks passed into async functions to handle async results.
- Instead of nesting callbacks, we can **chain promises** for a sequence of async operations - escaping _callback hell_.

## The Event Loop

Whenever the call stack is empty the event loop takes callbacks from the callback queue and puts them in the call stack so that they can be executed. The event loop is the essential piece that makes asynchronous behaviour possible in JS.

### Callback queue

A callback queue is an ordered list of callbacks waiting to be executed in/by the callstack.

## [Microtasks](https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API/Microtask_guide)

### Microtask queue

A microfunction is a function that is executed AFTER its calling function has exited, but before any other task in the callback queue. Microtasks are kept in the microtask queue, which is similar to the callback queue, except it has priority over the callback queue. When running JS code top-level code is run before executing the tasks in the microtask queue.
A microtask queue is where callbacks related to promises go. It has priority over the callback queue.

> First, each time a task exits, the event loop checks to see if the task is returning control to other JavaScript code. If not, it runs all of the microtasks in the microtask queue. The microtask queue is, then, processed multiple times per iteration of the event loop, including after handling events and other callbacks.

Second, if a microtask adds more microtasks to the queue by calling queueMicrotask(), those newly-added microtasks execute before the next task is run. That's because the event loop will keep calling microtasks until there are none left in the queue, even if more keep getting added.

Example:

```javascript
console.log("Test start");
setTimeout(() => console.log("0 sec timer"), 0);
Promise.resolve("Resolved promise 1").then((res) => console.log(res));
Promise.resolve("Resolved promise 2").then((res) => {
  for (let i = 0; i > 100000000; i++) {}
  console.log(res);
});
console.log("Test end");
```

If we run the example above, the order of execution as follows:
First console.log()-s are executed, because they are top level-level codes. Then come the Promises, because their resolve tasks are queued in the microtask queue, which has priority over the callback queue. Last executed is the setTimeout().

Microtasks are rarely interacted with by developers, yet there are some use-cases when timing of tasks that are executed together is critical.

# Modern JavaScript Development

## Overview

First we **develop** modules which go through a **build process**. First step of the build process is **bundling** all modules together. This process eliminates unused code and compresses our code as well. This is important because olderbrowsers do not support modules.
Second step is **transpiling and polyfilling**, which means converting all modern JS syntax back to old ES5 syntax. It is usually done by _Babel_. Tools used for the build process: _webpack_ or _PARCEL_. They are called js bundles as well, because they take our code and transform it into a js bundle.

## Modules

A **module** is a reusable piece of code that **encapsulates** implementation details. It is usually a **standalone file.** In such modules we can **import** and **export** values (so basically = react components). Whatever we export from a module is called **public API.** Modules from which we import and use are called **dependencies.**

Modules are favoured because:

- They can be used to **compose software.** They are small building blocks
- Modules can be developed entirely **separately**, without having to understand how other components work
- Use of modules leads to a more **organized code**
- They allow for easy **reuse**
- **Abstract code**. Other modules can use the low level code without understanding it.

### Difference between modules and scripts:

| | ES6 MODULE | SCRIPT |
| Top-level variables | Scoped to module | Global |
| Default mode | Strict mode | "Sloppy" mode |
| Top-level _this_ | undefined | window |
| Imports and exports | YES | NO |
| HTML linking | <script type ="module"> | <script> |
| File downloading | Async | Sync |

Modules are **imported synchronously, while downloaded asynchronously!**

Importing **erything** from a module into an object example:

```javascript
import * as ShoppingCart from "./shoppingCart.js";
```
