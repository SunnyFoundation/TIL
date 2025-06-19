# required

⚡️ Makes all properties in T required.






``` typescript 
interface User {
    id: number;
    name?: string;
    email?: string;
}

const user: Required<User> = {
    id: 1,
    name: "John Doe",
    email: "sunkim1055@gmail.com",
};

```


