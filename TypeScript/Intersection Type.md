# Intersection type










``` typescript 
type Dog = {
    name: string;
    color: string;
};

type Cat = {
    name: string;
    age: number;
};
type Pet = Dog & Cat;

let myPet: Pet = {
    name: 'Buddy',
    color: 'Brown',
    age: 3
};


```
