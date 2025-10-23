# Scope
* Local
* Global
* Package



## Local 
```go
package main


import "fmt"


func main() {
    message := "Hello"
    fmt.Println(message) //  가능
}


// fmt.Println(message)  불가능 (main 함수 밖에서는 안 보임)


```



## Global 
```go
// greet/greet.go
package greet


var Hello = "Hello, world!" // Exported (대문자로 시작) → 외부 패키지에서 접근 가능
var secret = "shh..."       // Unexported (소문자) → 내부 전용




// main.go
package main


import (
    "fmt"
    "myapp/greet"
)


func main() {
    fmt.Println(greet.Hello)  //  접근 가능
    // fmt.Println(greet.secret)  접근 불가
}



```


## Package 
```go
package main


import "fmt"


var greeting = "Hi" // 패키지 스코프


func sayHello() {
    fmt.Println(greeting) //  접근 가능
}


func main() {
    fmt.Println(greeting) //  접근 가능
    sayHello()
}



```
