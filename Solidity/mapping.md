# mapping 
⚡️ when you input key you can get output as value 



```solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract mapping {
   
   mapping(address => string) public name;
   
   function addName(address _key, string memory _name) public {
       name[_key] = _name;
   }
   
   function getName(address _key) public view returns(string memory) {
       return name[_key];
   }
}
```
