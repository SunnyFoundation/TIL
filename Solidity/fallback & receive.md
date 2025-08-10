# fallback 

⚡️ Function executed when a contract is called with a function that does not exist.


## receive 
 ⚡️  Function executed only when the contract receives pure ETH.
 






```solidity
// SPDX-License-Identifier: GPL-3.0

pragma solidity >=0.8.2 <0.9.0;

contract Example {
    event Fallback(string _str);
    event Receive(string _str);

    function addNumber(uint256 _num, uint256 _num2) public pure returns (uint256) {
        return _num + _num2;
    } 

    fallback() external {
        emit Fallback("fallback is called");
    }

    receive() external payable { 
        emit Receive("receive is called");
    }
}

contract Caller {
    event CalledFunction(bool _success , bytes _output); 

// receive is called
    function transferETH(address payable _to) public payable {
        (bool success ,) = _to.call{value : msg.value}("");
        require(success, "failed to transfer ether");
    }


  // fallback is called 
    function callMethod(address _contractAddr, uint256 _num1 , uint256 _num2) public {
        (bool success, bytes memory output) = _contractAddr.call(
            abi.encodeWithSignature("doesNotExist(uint256,uint256)", _num1, _num2)
        );
        require(success, "call to addNumber failed");
        emit CalledFunction(success, output);
    }
}


```








    




