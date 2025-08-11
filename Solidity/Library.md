# Library

⚡️ reuse code 
 * using [Library name ] for [type]
  


```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;


library Math {

    function add(uint a, uint b) internal pure returns (uint) {
        return a + b;
    }

    // 두 수를 곱하는 함수
    function multiply(uint a, uint b) internal pure returns (uint) {
        return a * b;
    }
}

// 2. 라이브러리를 사용하는 컨트랙트
contract Calculator {

    using Math for uint;

    uint public result;

    // 라이브러리 함수를 호출하는 방법
    function calculate(uint x, uint y) public {

        result = x.add(y); // = Math.add(x, y)
        

        result = result.multiply(y); // = Math.multiply(result, y); 
    }
}

```
