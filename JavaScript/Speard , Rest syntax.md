# What is spread syntax
 Get all the values in array 

### array spread

```jsx
let array = [1,2,3];

let array2 = [...array,4,5,6];

console.log(array2); // [ 1, 2, 3, 4, 5, 6 ]

```

### object spread 

```jsx
let animal = {
    name : 'rabbit',
    age : 1,
    owner : 'steve'
}

let animal2 = {
    ...animal,
    name1 : 'tiger',
    age2 : 2,
    owner1 : 'sun'
}

console.log(animal2)   // {
  name: 'rabbit',
  age: 1,
  owner: 'steve',
  name1: 'tiger',
  age2: 2,
  owner1: 'sun'
} 
```

# What is Rest syntax
 rest syntax  turns all the elements into an array.

```jsx
let array = [1,2,3];

function number(...rest) {
    console.log(rest);
}

number(...array);  // [ 1, 2, 3 ]

```
