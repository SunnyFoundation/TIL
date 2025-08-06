# variable
 ⚡️ Space that stroed data 

   * state variable
   * local variable
   * global variable




## state variable
 ⚡️ can access all of function | stored BlockChain  | stored storage 


```solidity
 contract MyStateVariable {
    uint256 public myNumber = 100;
}
```


## local variable
 ⚡️ can access inside of function | stored memory  | stored stack 


```solidity
function myLocalVariable (uint256 a, uint256 b) public pure returns (uint256) {
    uint256 sum = a + b; 
    return sum;
}
```



## global variable
 ⚡️ can read data of BlockChain 


```solidity
function setOwner() public {
    owner = msg.sender; 
}
}
```
