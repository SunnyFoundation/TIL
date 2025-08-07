# Reference Types.md  
 ⚡️ When you copy the original, the actual value isn't copied, but the address of the original is
  * array
  * struct
  * mapping



## array

```solidity
contract Example {
    uint[] public numbers;

    function update() public {
        uint[] storage nums = numbers; // nums Reference numbers address
        nums.push(1); // numbers array has been changed 
    }
}

```
