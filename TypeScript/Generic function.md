# Generic function








``` typescript 
// work with any type When you call the function you can get the type you want


function func<T>(value: T): T {
    return value;
}

let num = func<number>(10);
let str = func<string>('Hello');
let bool = func<boolean>(true);



```


