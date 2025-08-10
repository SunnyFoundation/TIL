# payable 

⚡️ You need to use this keyword when send ETH

* send
* transfer
* call

## send
 ⚡️ expand 2300 gas | return true or false 
 
## transfer
 ⚡️ expand 2300 gas | return error

  
## call
 ⚡️ variable gas expand | return true , false, byte
 






```solidity
contract payableTest {

    event howMuch(uint256 _value);

    function sendNow(address payable  _to) public payable {
        bool sent = _to.send(msg.value);
        require(sent,"Failed to send ETH");
        emit howMuch(msg.value);
    }

      function transferNow(address payable  _to) public payable {
         _to.transfer(msg.value);
        emit howMuch(msg.value);
    }

      function callNow(address payable _to) public payable {
    (bool sent, ) = _to.call{value: msg.value}("");
    require(sent, "Call failed");
    emit howMuch(msg.value);
}



  
  
}
```








    




