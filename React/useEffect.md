⚡️  when you managed component life cycle then You can useEffect
 






* `call back function`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; when component mounted  the callback function executed first

* `deps`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  [ ]  value in deps has changed callback function  is excuted 



* `Mount`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
 useEffect(()=>{
   console.log(“mount”);    
},[])  
```

* `update`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
useEffect(()=>{
    console.log(“update”);    
},[count]) // when count value has changed then console.log is excuted



```

  Why we use update instead of using useState
Because useState is excuted as asynchronous 
So you can’t respond data immediately 


* `unmount`

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
```javascript
useEffect(()=>{
    
return () => { console.log(“unmount”) } 
    
},[])



```



