# constructor

⚡️ The first function that runs when a contract is first deployed.
  
   * constructor
   * constant
   * immutable 




## constructor 
⚡️ The first function that runs when a contract is first deployed.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract constructor {
    

uint num = 5;

constructor (uint _num) {
 
 num = _num;

}

}
```




## constant 
⚡️ initial value is required.

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract constructor {
    
uint public constant = 5;

}

```


## immutable 
⚡️ Initial values are provided when the constructor is initialized

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract constructor {
    
 uint immutable public num; 

constructor (uint _num) {
 num = _num; 
}

}
```
