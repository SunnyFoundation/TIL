# ReturnType

⚡️ return  type that you want 




``` typescript 
function getUser() {
  return {
    name: "Sunny",
    age: 25,
  };
}

type User = ReturnType<typeof getUser>; // // User = { name: string; age: number }

```
