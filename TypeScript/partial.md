# partial

⚡️  Makes all properties in T optional.






``` typescript 
interface Post {
    id: number;
    title: string;
    content: string;
}


const draft : Partial<Post> = {
    id: 1,
    title: "My first post"
};
```


