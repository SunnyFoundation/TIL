# Upcasting



⚡️ Number type is a super type (parent type)
  Literal type is a sub type (child type)

Assigned children type to parent type





``` typescript 
let num1 : number = 10;
let num2 : 10 = 10; 

num1 = num2; // possible as num2 is child type
```


# Downcasting

⚡️ Assigned parent type to children type




``` typescript 

num2 = num1; // Not possible as num2 is child type
```
