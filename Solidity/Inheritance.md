# Inheritance 


⚡️ it allows child contract can use all of variable , function from parent funciton 
  *  Inheritance
  *  Multiple Inheritance
  *  super


##  Inheritance
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


## Multiple Inheritance
```solidity
contract Father {
    uint256 fatherMoney = 100;


   function getMoney() public virtual  view returns (uint256) {
      return fatherMoney;
   }

   
    
}

contract Mother {
    uint256 motherMoney = 300;


   function getMoney() public virtual  view returns (uint256) {
      return motherMoney;
   }
    
}



contract Son is Father,Mother {

   
    function getMoney() public override(Father,Mother)  view returns (uint256) {
      return fatherMoney + motherMoney;
   }

 
}
```


##  super
⚡️ You can avoid the hassle of inheriting multiple lines of code by using the super keyword.



```solidity

    
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.2 <0.9.0;

/**
 * @title Storage
 * @dev Store & retrieve value in a variable
 * @custom:dev-run-script ./scripts/deploy_with_ethers.ts
 */


contract Father {
    event FatherName(string name);

    function who() public virtual {
        emit FatherName("KIM-KI-EUN");
    }
}


    









contract Son is Father {
    event SonName(string name);

    function who() public override {
        super.who(); // Father의 who 호출
        emit SonName("Sunny"); // Son의 이벤트 발행
    }
}
```





