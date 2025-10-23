# Struct 


```go
package main


import "fmt"


type User struct {
    firstName string
    lastName  string
    email     string
    tickets   uint
}


func main() {
    // 1️⃣ 구조체 생성
    user1 := User{
        firstName: "Sunny",
        lastName:  "Kim",
        email:     "sunny@email.com",
        tickets:   2,
    }


    // 2️⃣ 필드 접근
    fmt.Println(user1.firstName)
    fmt.Println(user1.lastName)
    fmt.Println(user1.email)
    fmt.Println(user1.tickets)


    // 3️⃣ 전체 출력
    fmt.Printf("%+v\n", user1) // %+v : 필드 이름과 값 같이 출력
}


```
