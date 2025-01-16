# Understanding Type Casting in JavaScript

Type casting can change the type to another type.

Like changing numbers into words, or words into numbers.

```javascript
let age = 25;
let changeToString = String(age); // "25"

let two = "2";
let five = "5";
let age = Number(two + five); // 25

console.log(age);
