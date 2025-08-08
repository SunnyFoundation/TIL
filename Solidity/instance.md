# Instance 
⚡️ can Access one Contract from another Contract 




``` solidity

contract A {

     uint256 public  a = 3;

     function changeA(uint256 _num) public  {
         a = _num;
     }
}



contract B {
   A instance = new A();

   function getA() public  view  returns (uint256) {
      return instance.a();
   }


   function changeA(uint256 _num) public {
        instance.changeA(_num);
   }
}

```
