# Functions

## Key Points
1. A function is a block of code that performs a specific task.
2. Declaring a function.
3. Calling a function.
4. Arguments.
5. Parameters.
6. Return values.

---

### 1. A Function is a Block of Code

Let's start simple. We will create a function that prints "hello world!".

### 2. Declaring a Function

```javascript
function hello() {
    console.log("hello world!");
}
```

#### Steps:
1. Use the `function` keyword.
2. Give the function a name (e.g., `hello()`).
3. Write the desired code inside curly braces `{}`.

In this example, the function `hello` is a block of code that prints "hello world!". However, declaring a function is not enough. We need to **call** the function to make it run.

---

### 3. Calling a Function

Calling a function is very simple. Just write the function name followed by parentheses:

```javascript
hello();
```

This will execute the `hello` function and print:

```
hello world!
```

---

### 4. Arguments

Let's look at a more practical example. Imagine we want to calculate the area of a rectangle.

```javascript
function getArea() {
    let area = 10 * 10;
    console.log(area);
}

getArea(); // 100
```

When we run `getArea()`, the function calculates `10 * 10` and prints `100`. 

But what if we want to set the length and width dynamically instead of keeping them fixed at `10`? This is where **arguments** and **parameters** come in.

To calculate a rectangle with width `20` and height `20`, we need to pass these values to the function:

```javascript
getArea(20, 20);
```

---

### 5. Parameters

The function also needs to **receive** the values we pass. Think of it like playing catch—someone throws the ball, and someone else catches it. 

Here’s how the function can catch the values:

```javascript
function getArea(width, height) {
    let area = width * height;
    console.log(area);
}
```

#### Explanation:
- The `width` and `height` inside the parentheses are **parameters**.
- When calling `getArea(20, 20)`, the values `20` and `20` are passed into the parameters `width` and `height`.
- The function uses these parameters to calculate the area.

This way, the function is no longer fixed to `10 * 10`. Instead, it calculates the area based on the values passed during the function call. 

- Values passed to the function: **Arguments**.
- Variables inside the function that catch these values: **Parameters**.

---

### 6. Return Values

Previously, we used `console.log` inside the function just to test the output. However, the actual result of a function is returned using the `return` keyword.

For example:

```javascript
function getArea(width, height) {
    let area = width * height;
    return area;
}
```

#### Example with Return Value:

```javascript
let squareArea = getArea(20, 20);
console.log(squareArea); // 400
```

#### Explanation:
- The function calculates `20 * 20` and returns the result (`400`).
- The returned value is stored in the variable `squareArea`.
- We then print `squareArea` to the console, which outputs `400`.

---
