# Visibility Specifiers
 ⚡️ keyword that specify  access range of variable or function 

   * public
   * private
   * external
   * internal




## public
 ⚡️ accessible from anywhere, both inside and outside the contract.


```solidity
uint256 public myNumber; 

function getNumber() public pure returns (uint256) {
    return 100;
}
```


## private
 ⚡️ accessible from inside of contract  
 
```solidity

contract MyPrivate {

  uint256 private mySecretNumber = 42;

function _getSecretNumber() private view returns (uint256) {
    return mySecretNumber;
}

}
```



## internal 
 ⚡️ accessible from both inside of contract and inherited contract  


```solidity
contract Myage {

    uint256 public age = 23;

    function setAge(uint256 _age) internal {
         age = _age;
    }
    
}


contract Myage2 is Myage {
     constructor() {
        setAge(26);
    }
}
```



## external 
 ⚡️ It is only accessible from the outside.

```solidity
function sendMoney() external payable {
    // It is only accessible from the outside.

}
```
