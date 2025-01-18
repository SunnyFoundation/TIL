# Callback Functions

## Key Point
A **callback function** is a function that gets executed later by another function.

For example, here is a simple function:

```javascript
function callback() {
    console.log('call me later~');
}
```

This `callback` function will be executed by another function later. 

Now, let’s write a function that will **call the callback function**:

```javascript
function iMissYou(callback) {
    callback();
}
```

Here’s how it works:
- `iMissYou` is a function that takes another function (like `callback`) as an argument.
- Inside `iMissYou`, the `callback` function is executed.

To use it:

```javascript
iMissYou(callback);
```

#### Explanation:
- We pass the `callback` function as an argument to `iMissYou`.
- `iMissYou` runs the `callback` function, which prints:

```
call me later~
```

This is how callback functions work—they are passed as arguments and executed later by another function.

---
