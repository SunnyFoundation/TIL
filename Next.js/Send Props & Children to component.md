# 📦 Send Props & Children to component 




```tsx
function MyComponent({ name, children }: { name: string; children: React.ReactNode }) {
  return (
    <div>
      <h1>Hello, {name}!</h1>
      <div>{children}</div>
    </div>
  );
}

// Usage
<MyComponent name="Sunny">        // props
  <p>This is children.</p>    // children 
</MyComponent>
```
