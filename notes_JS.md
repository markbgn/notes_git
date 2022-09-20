# JavaScript notes
Here I will be retaking the notes I have taken during my Complete JavaScript course for documentation and rehearsal.
## Instance methods
Instance methods will be added to the prototype property, so all instances can use them.
## Static methods
Static methods are not added to the prototype property, thus they are not available for the instances (of classes for example)

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
