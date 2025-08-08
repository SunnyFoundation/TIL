# overriding

⚡️ When you want to keep the inherited function but add new code to it, you use virtual and override.
```solidity
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

   function getMoney() public virtual  view returns (uint256) {
      return money;
   }

   
    
}



contract Son is Father("SUN") {

   uint256 public earning = 0;

   function work() public {
     earning += 100;
   }

    function getMoney() public override  view returns (uint256) {
      return money+earning;
   }



   
   function sayHello()  public pure returns (string memory) {
      return "I'm SUN!";
   }
 
}



```
