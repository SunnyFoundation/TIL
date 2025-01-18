# Objects

## 1. What is an Object?

An object represents a single topic with multiple categories. For example:
- `book` (categories: `comedy`, `romance`, `true story`)
- `world` (categories: `USA`, `South Korea`, `Japan`, `China`)

---

## 2. Object Properties

Objects contain **properties**, which represent the categories. For example:

```javascript
let person = {
    name: 'sun',
    age: 25,
    job: "blockchain engineer",
};
```

- **Object**: `person`
- **Properties**: `name`, `age`, `job`
- **Values**: `'sun'`, `25`, `'blockchain engineer'`

Here, properties are written as key-value pairs:
- Key: `name`
- Value: `'sun'`

---

## 3. Accessing Properties

### 1. Dot Notation

```javascript
let person = {
    name: 'sun',
    age: 25,
    job: "blockchain engineer",
};

let a = person.job; // "blockchain engineer"
```

### 2. Bracket Notation

```javascript
let person = {
    name: 'sun',
    age: 25,
    job: "blockchain engineer",
};

let a = person["name"]; // "sun"
console.log(a);
```

---

## 4. Methods

When a property’s value is a function, it is called a **method**.

```javascript
let person = {
    name: 'sun',
    age: 25,
    job: "blockchain engineer",
    hi: () => {
        console.log("hello world");
    },
};

let a = person.hi(); // "hello world"
console.log(a);
```

---
