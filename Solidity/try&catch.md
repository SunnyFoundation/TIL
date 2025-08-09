# try&catch
⚡️Executes an external contract and handles the error if the execution fails.




```solidity
pragma solidity ^0.8.0;

// 외부 컨트랙트 예시
contract Math {
    function div(uint256 a, uint256 b) public pure returns (uint256) {
        require(b != 0, "b can't be zero"); // 0으로 나누기 방지
        return a / b;
    }
}

// try-catch 사용하는 컨트랙트
contract Tester {
    Math math = new Math();

    event Success(uint256 result);
    event CatchError(string reason);

    function safeDivide(uint256 a, uint256 b) public returns (uint256) {
        try math.div(a, b) returns (uint256 result) {
            emit Success(result);
            return result;
        } catch Error(string memory reason) {
            // require, revert 같은 에러 메세지 잡기
            emit CatchError(reason);
            return 0;
        } catch {
            // 예상치 못한 에러 잡기
            emit CatchError("Unknown error");
            return 0;
        }
    }
}

```
