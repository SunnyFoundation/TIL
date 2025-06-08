⚡️ When using so many useState then your code is so complex and dirty so here is came called useReducer  




* `useReducer`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
const [state, dispatch] = useReducer(reducer,0);


```


* `Reducer`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
function reducer(state, action) {
    switch (action.type) {
        case 'INCREMENT':
            return state + action.payload;
        case 'DECREMENT':
            return state - action.payload;
        default:
            throw new Error();
    }
}

```




* `Dispatch`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
  const onClickPlus = () => {
    dispatch({
        type: 'INCREMENT',
        payload: 1,
    });
}


  return (
    <div>
        <button onClick={onClickPlus}>+</button>
    </div>
  )
}

```
