# Array & Slice 

* Array
* Slice




## Array 
```go
package main


import "fmt"


func main() {
    // 길이가 3인 int 배열
    var nums [3]int
    nums[0] = 10
    nums[1] = 20
    nums[2] = 30


    fmt.Println(nums)      // [10 20 30]
    fmt.Println(nums[1])   // 20


    // 배열 리터럴
    names := [3]string{"Alice", "Bob", "Charlie"}
    fmt.Println(names)     // [Alice Bob Charlie]


    // 길이를 생략하면 컴파일러가 자동으로 계산
    primes := [...]int{2, 3, 5, 7, 11}
    fmt.Println(primes)    // [2 3 5 7 11]
}


```










## Slice 
```go
package main


import "fmt"


func main() {
    // 슬라이스 선언과 초기화
    nums := []int{10, 20, 30}
    fmt.Println(nums)  // [10 20 30]


    // append로 요소 추가
    nums = append(nums, 40)
    fmt.Println(nums)  // [10 20 30 40]


    // 부분 슬라이스 (기존 배열 또는 슬라이스의 일부)
    sub := nums[1:3]
    fmt.Println(sub)   // [20 30]


    // 길이와 용량 확인
    fmt.Println(len(nums)) // 4
    fmt.Println(cap(nums)) // 4 (capacity, 내부 배열의 실제 크기)


    // make로 슬라이스 생성 (길이, 용량 지정)
    s := make([]int, 3, 5)
    fmt.Println(s) // [0 0 0]
}

```

