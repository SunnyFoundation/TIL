# Arrow Functions

## Definition
Arrow functions are a shorter way to write functions. They are simpler and don’t need a name.

## Key Point 1
Arrow functions remove the need for a function name. Instead, we use an arrow `=>`.

### Example 1: Regular Function

```javascript
function hello() {
    console.log('hello javascript');
}

hello();
```

### Example 2: Arrow Function

```javascript
let narrowFunction = () => {
    console.log('hello narrow function');
};

narrowFunction();
```

#### Explanation:
- The `function` keyword is removed.
- The arrow `=>` is used after the parentheses `()`.
- The result is a shorter, easier-to-read function.

This is why arrow functions are often preferred in modern JavaScript.

---
