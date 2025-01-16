# Understanding `let` and `const` in JavaScript

In JavaScript, `let` and `const` are used to declare variables. Think of them as **data boxes** that contain information.

## `let`

- `let` is a data box that can change the data it contains.
- Example:
  ```javascript
  let age = 25; // contains age data
  age = 26;     // changes the data
  console.log(age); // Output: 26
  ```

## `const`

- `const` is a data box that cannot change the data it contains once it has been assigned.
- Example:
  ```javascript
  const birth = "2000.03.02"; // contains birth data
  birth = "3000.03.02";       // Error! Cannot reassign a constant.
  console.log(birth); // Output: "2000.03.02"
  ```

