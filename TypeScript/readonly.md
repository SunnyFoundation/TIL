# readonly

⚡️  Makes all properties in T read-only.






``` typescript 
interface Todo {
    id: number;
    title: string;
    completed: boolean;
}

const todo: Readonly<Todo> = {
    id: 1,
    title: "Learn TypeScript",
    completed: false,
};
```


