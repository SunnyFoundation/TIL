# indexed access types


⚡️ accessing  property of an object type





``` typescript 
type Person = {
  name: string;
  age: number;
  address: {
    street: string;
    city: string;
  };
};

type PersonName = Person['name']; // string
type PersonAge = Person['age']; // number
type PersonStreet = Person['address']['street']; // string
```

