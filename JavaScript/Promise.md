# JavaScript Promise

## What is a Promise?

A **Promise** is a JavaScript object used for handling **asynchronous operations**.

Promises have **three key components**:

1. **State**
2. **Producer**
3. **Consumer**

---

## 1. State

The **state** represents the progression of an asynchronous operation:
- `Pending`: The initial state, waiting for completion.
- `Fulfilled`: The operation completed successfully.
- `Rejected`: The operation failed.

---

## 2. Producer

The **producer** is responsible for creating and initiating an asynchronous operation.

### 2.1 Creating a Promise

A Promise takes a callback function with two parameters (`resolve` and `reject`).

```javascript
const promise = new Promise((resolve, reject) => {
    // Asynchronous operation here
});
```

### 2.2 `resolve`

The `resolve` function is called when the asynchronous operation completes successfully.

```javascript
const promise = new Promise((resolve, reject) => {
    console.log('doing something');

    setTimeout(() => {
        resolve('sun');
    }, 2000);    
});
```

### 2.3 `reject`

The `reject` function is called when the asynchronous operation fails.

```javascript
const promise = new Promise((resolve, reject) => {
    console.log('doing something');

    setTimeout(() => {
        reject('error');
    }, 2000);    
});
```

---

## 3. Consumer

The **consumer** is responsible for handling the result of the Promise.

### Handling a successful Promise (`resolve` case)

```javascript
promise.then((value) => {
    console.log(value); // sun
});
```

### Handling a failed Promise (`reject` case)

```javascript
promise.catch(() => {
    console.log('error');
});
```
