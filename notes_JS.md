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