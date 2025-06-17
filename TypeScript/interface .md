# interface








``` typescript 
interface Person {
    name: string;
    age: number;
}

const person: Person = {
    name: 'SUN',
    age: 25,
};

```


# interface extension






``` typescript 

interface Employee extends Person {
    employeeId: number;
}

const employee: Employee = {
    name: 'SUN',
    age: 25,
    employeeId: 17,
};
```
