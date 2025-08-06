# Modifier 
⚡️ Adding Special Logic before and after executing fucntion 
 * pure
 * view




## pure

⚡️ You can only control varible in your funciton 


```solidity
 function myPure(uint a) public pure returns(uint) {
  return a
}
```


## view

⚡️ You can take external varible but dosen't update varible


```solidity

  uint public a = 3

 function myView() public view returns(uint) {
   uint b = a + 3
   return b 
}
```
