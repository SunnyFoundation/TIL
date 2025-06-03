⚡️ When using so many useState then your code is so complex and dirty so here is came called useReducer  




* `useReducer`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
  const initialState = { count: 0 };

  const [state, dispatch] = useReducer(reducer, initialState);

```


* `Reducer`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
// 💡 Receive respond and deal with it 

 const reducer = (state, action) => {
    switch (action.type) {
      case 'increment':
        return { count: state.count + 1 };
      case 'decrement':
        return { count: state.count - 1 };
      default:
        throw new Error();
    }
  };


```




* `Dispatch`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
// 💡send request

 <button onClick={() => dispatch({ type: 'increment' })}>Increment</button>
      <button onClick={() => dispatch({ type: 'decrement' })}>Decrement</button>


```
