# Event

⚡️ At a certain point, we save specific data to the blockchain



```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract event {
    
  event myFuction(uint result , string name)

function add(uint a , uint b) public {
  
    uint  total =  a + b;
   emit myFuction(total , add)
}

}

```
