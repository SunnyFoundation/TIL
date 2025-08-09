# ErrorHandler
⚡️ If an error occures the program terminates
 * assert
 * revert
 * require


## require
⚡️ when function first excuted the require check first strictly | refund gas fee 


```solidity
  function requireTest(uint256 a) public pure{
        require(a == 7,"a isn't 7");
    }
```


## revert
⚡️ Throw an error immediately without any condition  | refund gas fee 

```solidity

  function revertTest() public pure{
        revert("error!!");
    }

```


## assert
⚡️ Emergency! the critical error occured!   | not refund gas fee 

```solidity

function assertTest(uint a) public pure{
        assert(a == 7);
    }

```



