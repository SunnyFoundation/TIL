# function call signature








``` typescript 
type callSignature = {
    (x: number, y: number): number;
};

const add3: callSignature = (x, y) => {
    return x + y;
}
```

