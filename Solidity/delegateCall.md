# delegateCall

⚡️ borrow code  change my storage data 

```solidity

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;



contract Library {
    uint public num; // 이건 Library 자신의 num

    function setNum(uint _num) public {
        num = _num;
    }
}

contract TestCall {
    uint public num; // 내 num

    function callSetNum(address _lib, uint _num) public {
        // Library의 상태를 바꿈
        (bool success, ) = _lib.call(
            abi.encodeWithSignature("setNum(uint256)", _num)
        );
        require(success, "Call failed");
    }
}


contract TestDelegateCall {
    uint public num; // 내 num

    function delegateCallSetNum(address _lib, uint _num) public {
        // Library의 코드를 빌려서, 내 상태를 바꿈
        (bool success, ) = _lib.delegatecall(
            abi.encodeWithSignature("setNum(uint256)", _num)
        );
        require(success, "Delegatecall failed");
    }
}




```
