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
    calcAge() { // function
        console.log(2022-this.birthYear);
    }

    // Static method
    static hey() {
        console.log('Hey there!');
        console.log(this);
    }
}

const jessica = new PersonCl('Jessica Davis', 1999);

jessica.calcAge();
PersonCl.hey();
```


## Encapsulation in JavasCript (not yet official)
Encapsulation is currently being developed in JavaScript is at stage 3/4.

There are:
- Public fields (instances): declared at the beginning of the class without a *const* or *let*
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
    Basic technique for creating objects from functions. In the following example *Car* is a **constructor function**, which has a prototype property (*Car.prototype*). This is an **object**, inside which we have the *accelerate* and the *brake* methods. *Car.prototype* has a reference back to *Car* (*.constructor*)

    When we use the *new* keyword a new, empty object is created. Then the *this* keyword is set to the newly created object. An object's .__proto__ will point to its constructor(miata.__proto__ will point to *Car.prototype*). This way a **prototype chain** is formed.
    Example:
    ```javascript
    const Car = function(make, speed) { // Car constructor function is created
        this.make = make;
        this.speed = speed;
    };

    Car.prototype.accelerate = function() { // accelerate function is added to Car constructor function
        console.log(this.speed += 10);
    };

    Car.prototype.brake = function(decelaration=10) { // brake function is added to Car constructor function
        console.log(this.speed-decelaration);
    };

    const miata = new Car('Miata', 230);
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
        constructor (make, speed) { // Constructor sets the base values
            this.make = make;
            this.speed = speed;
        }

        accelerate() { // accelerate function is defined and available for instances of CarCL
            console.log(this.speed += 10);
        }

        brake() { // brake function is defined and available for instances of CarCL
            console.log(this.speed -=10);
        }
    };
    ```

## Inheritance with JavaScript classes (constructor functions)

## Get & Set