# Union Type









``` typescript 
function printId(id: number | string): void {
    console.log(`Your ID is: ${id}`);
}
printId(101); // Valid
printId('202'); // Valid
 printId(true); // Invalid
```

