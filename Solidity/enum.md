# enum
⚡️ Categorized, starting from index 0

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract OrderExample {
    // 주문 상태 정의
    enum Status { 
        Pending,
        Shipped, 
        Delivered, 
        Cancelled 
    }

    Status public orderStatus;

    // 초기 상태는 Pending (0번 인덱스)
    constructor() {
        orderStatus = Status.Pending;
    }

    // 주문 배송 처리
    function shipOrder() public {
        require(orderStatus == Status.Pending, "Order not pending");
        orderStatus = Status.Shipped;
    }

    // 주문 배송 완료 처리
    function deliverOrder() public {
        require(orderStatus == Status.Shipped, "Order not shipped");
        orderStatus = Status.Delivered;
    }

    // 주문 취소
  function cancelOrder() public {
        require(orderStatus != Status.Delivered, "Order already delivered");
        orderStatus = Status.Cancelled;
    }
    // 현재 상태를 숫자로 확인
    function getStatusNumber() public view returns (uint) {
        return uint(orderStatus);
    }
}

```
