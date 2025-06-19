# readonly

⚡️ Creates a type by picking keys K from type T.






``` typescript 
interface Product {
    id: number;
    name: string;
    price: number;
    description?: string;
}

const product: Pick<Product, 'id' | 'name'> = {
    id: 1,
    name: "Laptop",
};
```
