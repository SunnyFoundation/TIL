
##  Switch Statement

**Key Points**:
1. Put a variable inside the parentheses of `switch`.
2. Write the code for each case after the `:`.
3. By default, `switch` will check all cases unless you use the `break` keyword to stop.
4. If no cases match the variable, the `default` code will run.

Example:
```javascript
let animal = 'lion';

switch (animal) {
    case "lion":
        console.log("I'm lion");
        break;
    case "rabbit":
        console.log("I'm rabbit");
        break;
    case "tiger":
        console.log("I'm tiger");
        break;
    default:
        console.log("Unknown animal");
}
```

Explanation:
- `switch` checks the value of `animal`.
- If `animal` is "lion", it will print `"I'm lion"` and stop because of `break`.
- If `animal` is "rabbit" or "tiger", it will print the corresponding message.
- If `animal` doesn't match any case, it will print `"Unknown animal"`.
