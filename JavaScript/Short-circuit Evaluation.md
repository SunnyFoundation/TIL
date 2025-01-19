# What is Short-circuit Evaluation

and operator **spitting out true if two condition is true** 

or operator spitting out true if only one condition is true

In and operator Short-circuit Evaluation spitting out false without looking second condition if first codintion is false  

on the other hand Short-circuit Evaluation spitting out true without looking second condition if first condition is true 

```jsx
let a = true;

let b = false;

console.log(b && a);    // false

console.log(a || b);   // true 

```

# feature of Short-circuit Evaluation

In “&&” operator  if two condition true then second condition excuted 

In “||” operator  if two condition true then first condition excuted 

## &&

```jsx
let a = "A"

let b = "B";

console.log(a && b);    //  B
```

## ||

```jsx
let a = "A"

let b = "B";

console.log(a || b);    //  A
```
