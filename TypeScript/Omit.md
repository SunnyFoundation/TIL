# Omit

⚡️ Creates a type by omitting keys K from type T.






``` typescript 
type Person = {
  name: string;
  age: number;
  password: string;
};


type PublicPerson = Omit<Person, "password">;


const person: PublicPerson = {
  name: "Sunny",
  age: 25,
};
```
