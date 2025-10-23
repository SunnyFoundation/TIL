# function 

* Basic
* Multi Return



## Basic
```go
package main


import "fmt"


// 이름을 받아서 인사하는 함수
func greet(name string) {
    fmt.Println("Hello,", name, "!")
}


func main() {
    greet("Sun")   // Hello, Sun !
    greet("Alice") // Hello, Alice !
}


```



## Multi Return
```go
package main


import "fmt"


// 나눗셈 결과를 몫과 나머지로 반환
func divide(a, b int) (int, int) {
    quotient := a / b
    remainder := a % b
    return quotient, remainder
}


func main() {
    q, r := divide(10, 3)
    fmt.Println("Quotient:", q, "Remainder:", r)
}



```
