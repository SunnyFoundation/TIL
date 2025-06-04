⚡️  send data between components  
   &nbsp;&nbsp;&nbsp; props only send one way that parents send a data to child components  
&nbsp;&nbsp;&nbsp; but context every components should get a data from context







* ```Javascript
  const ThemeContext = createContext() // make context
  ```

* ```Javascript
  <ThemeContext.Provider value={{isDark, setIsDark}}>
    <Page />
   </ThemeContext.Provider> // You have to wrap with Provider to all of components


 * ```Javascript
   const data = useContext(ThemeContext) // when components use data from context you have to use useContext()
