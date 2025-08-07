#  mapping 

⚡️ A struct lets you group different types of variables together 




```solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract struct {
   
   struct MintCoin {
       string coinName;
       uint price;
   }
   
   MintCoin[] public openMarket;
   
   function addCoin(string memory _coinName, uint _price) public {
       openMarket.push(MintCoin(_coinName, _price));
   }
   
   function getCoin(string memory _coinName) public view returns(uint) {
       for(uint i = 0; i < openMarket.length; i++) {
           if(keccak256(abi.encodePacked(openMarket[i].coinName)) == keccak256(abi.encodePacked(_coinName))) {
               return openMarket[i].price;
           }
       }
       return 0; // 코인을 찾지 못한 경우
   }
}
```
