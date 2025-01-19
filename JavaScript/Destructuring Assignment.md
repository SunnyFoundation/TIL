# What is Destructuring Assignment

A method of breaking down the values of an array or an object and easily assigning them to variables.

### Array Destructuring

```jsx
const array = [1, 2, 3];
const [a, b, c] = array;

console.log(a); // 1
console.log(b); // 2
console.log(c); // 3

```

### Object Destructuring

```jsx
const obj = {
   name : 'sun',
    age : 25,
   sex : 'man'
 }
 
 
 let { name ,age , sex } = obj; 
 
 
 
 
  console.log(name,age,sex); // sun 25 man

```
