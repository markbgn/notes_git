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
