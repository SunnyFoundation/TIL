# key of 


⚡️ it returns a union of the keys of the object type






``` typescript 
type Person = {
  name: string;
  age: number;
  address: {
    street: string;
    city: string;
  };
};

type PersonKeys = keyof Person; // 'name' | 'age' | 'address'

```

