# function overload








``` typescript 
//same function name, different parameter types
function add4(x: number, y: number): number;
function add4(x: string, y: string): string;

function add4(x: any, y: any): any {
    return x + y;
}

```

