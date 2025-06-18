# infer


⚡️ It returns the result of the ternary operator by inferring the type.






``` typescript 
type FuncA = () => string;
type FuncB = () => number;

type ReturnType<T> = T extends () => infer R ? R : never;
type ResultA = ReturnType<FuncA>; // string
type ResultB = ReturnType<FuncB>; // number


```
