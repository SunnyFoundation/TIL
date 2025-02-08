# Synchronous vs Asynchronous in JavaScript

## What is Synchronous?

JavaScript engine executes code **line by line**, meaning one line of code completes before the next line executes.

Example:

```javascript
console.log('1');
console.log('2');
console.log('3');
```

### Output:
```
1
2
3
```
This is called **Synchronous Execution** because the code is executed in order without skipping or delaying any line.

---

## What is Asynchronous?

Rather than executing code **line by line** and waiting like synchronous operations, **asynchronous operations** move immediately to the next line without waiting.

Example:

```javascript
console.log('1');

setTimeout(() => {
    console.log('3');
}, 3000);

console.log('2');
```

### Output:
```
1
2
3 (after 3 seconds)
```

The `setTimeout` function takes **a callback function and a delay time (ms)** as parameters. It schedules the callback function to run after the specified delay without stopping the execution of subsequent code.

### Synchronous vs Asynchronous Behavior:

If the code were **synchronous**, it would:
1. Output `1`
2. Wait **3 seconds**
3. Output `3`
4. Output `2`

However, since `setTimeout` works **asynchronously**, the output sequence is:
1. Output `1`
2. Output `2` **immediately**
3. After `3 seconds`, output `3`
