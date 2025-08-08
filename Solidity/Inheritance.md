# Inheritance 


⚡️ it allows child contract can use all of variable , function from parent funciton 



```solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.2 <0.9.0;

/**
 * @title Storage
 * @dev Store & retrieve value in a variable
 * @custom:dev-run-script ./scripts/deploy_with_ethers.ts
 */


contract Father {
   string public firstName = "KIM";
   string public givenName = "ki_un";
   uint256 public money = 100;

   function getFamilyName(string memory) view  public  returns (string memory) {
      return firstName;
   }

   function getGivenName(string memory) view public returns (string memory) {
      return givenName;
   }

   constructor(string memory _givenName)  {
        givenName = _givenName;
   }

   
    
}



contract Son is Father("SUN") {

   function sayHello()  public pure returns (string memory) {
      return "I'm SUN!";
   }
 
}
```
