⚡️ There is a variable that contain data and the function that is changing data if you change variable through function then component and their child will re-rendering

` const [count, setCount] = useState(0);`

 `const increase = () => {
    setCount(count + 1)
  };`

      <button onClick={increase}>+1</button>
