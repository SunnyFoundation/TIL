# mapped


⚡️ it returns a union of the keys of the object type






``` typescript 
type User = {
  name: string;
  age: number;
};

type UserFlags = {
  [K in keyof User]: boolean;
};


type UserFlags = {
  name: boolean;
  age: boolean;
};


```

