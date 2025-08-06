#  Data Location 

⚡️ It specifies where data will be stored. 
 * memory
 * storage
 * calldata
 * stack



## memory 
⚡️ For using reference types like arrays, mappings, and structs inside a function, you must specify memory.



```solidity

function getNames() public pure returns (string[] memory) {

        string[] memory names = new string[](3); 


        names[0] = "Sunny";
        names[1] = "Jobs";
        names[2] = "Musk";

        return names;
    }

```


## callData
⚡️ Read Only - External Data 



```solidity

function getNames(string calldata name) external pure returns (string memory) {

           return name
    }

```



## storage
⚡️  All data saved in BlockChain Storage 


```solidity

contract StorageExample {

    uint256 public number = 100;        // storage 
    string public name = "Sunny";       // storage

```



## stack
⚡️  Value type variables declared inside a function are automatically stored on the stack.


```solidity

contract Example {
    uint256 public myNumber; // storage

    function add(uint256 a, uint256 b) public {

        uint256 sum = a + b;  // stack
        myNumber = sum;
    }
}
```




