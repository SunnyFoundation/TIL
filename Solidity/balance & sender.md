# balance 


⚡️ User's bank balance


# msg.sender 


⚡️ Address of users who use function 




```solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.2 <0.9.0;




contract mobileBank {
 
  event sendInfo(address _msg.sender, uint256 _value);

function sendETH(address payable _to) public payable {
    require(msg.sender.banlance >= msg.value, "balance is not enough");
       _to.transfer(msg.value);
     event sendInfo(msg.sender,(msg.value).msg.value);
}

 
}
```








    




