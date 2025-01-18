# Scope

## Key Point
Think of scope like a castle. Variables inside a function are like Rapunzel inside her tower—they can’t be accessed from outside the castle.

### Example:

```javascript
let globalScope = 'global';

function local() {
    let localScope = 'local';
}

console.log(globalScope); // 'global'
console.log(localScope); // Error!!!
```

#### Why Does `localScope` Give an Error?
`localScope` is a variable inside the `local` function. You can’t access it from outside the function because it’s locked inside the function’s scope, just like Rapunzel is locked in her tower.

On the other hand, `globalScope` is outside the function, so anyone can access it.

---
