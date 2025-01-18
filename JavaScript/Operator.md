# Operators in JavaScript

## 1. Nullish Coalescing Operator (`??`)

**Key Point**: If the value on the left side of `??` is not `null` or `undefined`, it will use the left value. Otherwise, it will use the right value.

```javascript
let userName; 
let userNickName = "sunny"; 

let displayName = userName ?? userNickName; 
```

Explanation:
- `displayName` checks `userName` first.
- Since `userName` has no value (`undefined`), `displayName` will use `userNickName` instead.
- Result: `displayName` will be `"sunny"`.

## 2. `typeof` Operator

**Key Point**: This keyword tells you the type of a variable.

Examples:
```javascript
let whatIsType = "hello"; 
let answer = typeof whatIsType;  // "string"

let whatIsType = 25;
let answer = typeof whatIsType;  // "number"
```

Explanation:
- `typeof whatIsType` will check the type of the variable `whatIsType`.
- For example, if `whatIsType = "hello"`, `typeof` will return `"string"`.
- If `whatIsType = 25`, `typeof` will return `"number"`.

## 3. Ternary Operator (`? :`)

**Key Point**: If the condition before `?` is true, it will use the value on the left of `:`. Otherwise, it will use the value on the right.

```javascript
let robot = 4 / 2 === 2 ? "robot" : "human";
```

Explanation:
- `4 / 2 === 2` is true because `4 / 2` equals `2`.
- Since the condition is true, the value of `robot` will be `"robot"`.
- If the condition was false, `robot` would be `"human"`.
