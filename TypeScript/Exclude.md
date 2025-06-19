# Exclude

⚡️ Delete you want type And return all of type 





``` typescript 
type Fruits = "apple" | "banana" | "orange";
type NoBanana = Exclude<Fruits, "banana">;  // NoBanana = "apple" | "orange"

```
