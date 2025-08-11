# interface 
⚡️ every contract must follow this interface code for Standardization
 *  implement signature of function 


```solidity 

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;


interface ICounter {

   // implement signature of function 
    function increment() external;
    function getCount() external view returns (uint);
}




contract Counter is ICounter {
    uint private count;

    function increment() external override {
        count += 1;
    }

    function getCount() external view override returns (uint) {
        return count;
    }
}
```
