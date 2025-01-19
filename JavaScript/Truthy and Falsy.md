# What is Truthy and Falsy
They are not conditions but they are perceived as conditions in JavaScript.
## Example 01
```jsx
if (123) {
    console.log('123 is true')
} else {
    console.log('123 is false')
}
if (undefined) {
   console.log('undefined is true')
} else {
    console.log('undefined is false')
}
```
123 is not a condition but it is truthy, so JavaScript recognizes `123` as true.
undefined is not a condition but it is falsy, so JavaScript recognizes `undefined` as false.
## Example 02
```jsx
let person = null;
function name(person) {
    if(!person) {
       console.log('Person value exists')    
    } else {
        console.log(person.name)
    }
}
name(person)
```
If `null` enters the `if` statement, then `null` is a falsy value. So JavaScript recognizes `null` as false. However, the `null` value meets with the `!` operator, so `null` is recognized as true, and the `if` statement is executed.
