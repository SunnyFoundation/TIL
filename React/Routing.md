⚡️  User move another page 




* `Router`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
npm i react-router-dom
```

```javascript

  <BrowserRouter>
      <App />
  </BrowserRouter> // main.jsx 


```




* `Routes`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
 <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/diary" element={<Diary />} />
        <Route path="/new" element={<New />} />
 </Routes>  // App.jsx



```



* `Link`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
      <Link to="/">Home</Link>



```



* `useNavigate`
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
 const nav = useNavigate();


 const onclickButton = () => {
    nav('/new');
  }


```



* ` URL Parameter `
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript

 <Route path="/diary/:id" element={<Diary />} />

    const params = useParams();  

 return (
    <div>{params.id}Diary </div>
  )

```
