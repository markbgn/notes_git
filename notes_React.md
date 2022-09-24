# React notes

In this document I am taking notes while working through the [React course](https://www.udemy.com/course/react-the-complete-guide-incl-redux/) made by Maximilian Schwarzmüller.

## Exporting and importing

person.js:

```javascript
const person = {
  name: "Max",
};

export default person;
```

utility.js:

```javascript
export const clean = () => {...}
export const baseData= 10;
```

app.js:

```javascript
import person from "./person.js"; // The name does not matter as we only have one export
import prs from "./person.js";

import { clean } from "./utility.js"; // We directly specify the variable we want to import
import { baseData } from "./utility.js";
```

### Importing everything:

```javascript
import * as bundled from "./utility.js";
```

Important:

- A react component is just a JavaScript function!
- React components must start with an uppercase character, so that react is able to detect that it is a custom component.
- You must have **ONE** root element per react component
- When we pass values to a component, the received data comes as a object, which we call _props_ as a convention

## Children props

In order to place content between custom opening and closing tags, _{props.children}_ must be set in the definition of the component (between the tags).

## Defining EventListeners

For isntance a _click_ EventHandler can be addded this way:

```javascript
<button onClick={ClickHandler}>Change Title</button>
```

Where CliCkHandler is a function to be executed on a _click_ event.

## React State

Adding a named import:

```javascript
import React, { useState } from "react";
```

This way we import a function caled _useState_. This function allows us to define values as state, where changes to these values should result the component function being called again.

In the function of the component we can set that special variable with

```javascript
useStat(variable);
```

This function returns an array:

- The value itself
- The updating function

The returned function can be used on the returned value.
The useState(...) method takes the given value as an initial one during the first run of the component instance, than on re-runs it grabs the latest state, as it can detect that it had been initialized already before.

## Receiving data from inputs

The function which is being called by a _on..._ event receives the property called _event_, which among many things, holds the **value** of the input for the **target** in the moment of firing the event.
Example:

```javascript
const [enteredTitle, setEnteredTitle] = useState("");
const [enteredAmount, setEnteredAmount] = useState("");
const [enteredDate, setEnteredDate] = useState("");
//   const [userInput, setUserInput] = useState({
//     enteredTitle: "",
//     enteredAmount: "",
//     enteredDate: "",
//   });

const titleChangeHandler = (event) => {
  // Solution 1:
  setEnteredTitle(event.target.value);

  // Solution 2:
  // setUserInput({
  //   ...userInput, // spreading userInput data, then overriding enteredTitle.
  //   enteredTitle: event.target.value,
  // });

  // Solution 3:
  // setUserInput((prevState) => {
  //   return { ...prevState, enteredTitle: event.target.value };
  // });
};

const amountChangedHandler = (event) => {
  setEnteredAmount(event.target.value);
  // setUserInput({
  //   ...userInput,
  //   enteredAmount: event.target.value,
  // });
  // setUserInput((prevState) => {
  //   return { ...prevState, enteredAmount: event.target.value };
  // });
};

const dateChangedHandler = (event) => {
  setEnteredDate(event.target.value);
  // setUserInput({
  //   ...userInput,
  //   enteredDate: event.target.value,
  // });
  // setUserInput((prevState) => {
  //   return { ...prevState, enteredDate: event.target.value };
  // });
};
```

## Bubbling data up

## Controlled components

If a components logic is handled in the parent component, then it is called a **controlled component.**
