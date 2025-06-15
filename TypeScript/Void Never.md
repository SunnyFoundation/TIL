# void








``` typescript 
// A function that does not return a value 
function logMessage(message: string): void {
    console.log(message);
}

logMessage('Hello, TypeScript!');
```


# never



``` typescript 

// A function that never returns 
function throwError(message: string): never {
    throw new Error(message);
}
throwError('This is an error message');```
