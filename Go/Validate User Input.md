# Validate User Input
* strconv
* regexp
* strings



## strconv
```go
package main


import (
    "fmt"
    "strconv"     // String converse 
)


func main() {
    var input string
    fmt.Print("Enter your age: ")
    fmt.Scanln(&input)


    // 문자열을 숫자로 변환
    age, err := strconv.Atoi(input)  
    if err != nil {
        fmt.Println(" 숫자를 입력해주세요.") // Atoi 뜻: ASCII to integer (문자 → 숫자) 즉, "25" → 25
        return
    }


    // 나이 범위 검증
    if age < 0 || age > 120 {
        fmt.Println(" 나이는 0~120 사이여야 합니다.")
        return
    }


    fmt.Printf(" 당신의 나이는 %d세입니다.\n", age)
}


```


## regexp
```go
package main


import (
    "fmt"
    "regexp"  // Regular Expression  정규 표현식 
)


func main() {
    var email string
    fmt.Print("Enter your email: ")
    fmt.Scanln(&email)


    // 간단한 이메일 정규식 패턴
    re := regexp.MustCompile(`^[a-zA-Z0-9._%+\-]+@[a-zA-Z0-9.\-]+\.[a-zA-Z]{2,}$`)


    if !re.MatchString(email) {
        fmt.Println(" 올바른 이메일 형식이 아닙니다.")
        return
    }


    fmt.Println(" 이메일 형식이 올바릅니다.")
}




```




## strings
```go
package main


import (
    "fmt"
    "strings"
)


func main() {
    var name, country string
    fmt.Print("Enter your name: ")
    fmt.Scanln(&name)


    fmt.Print("Enter your country: ")
    fmt.Scanln(&country)


    if strings.TrimSpace(name) == "" {   // 이름은 공백이 올 수 없음 
        fmt.Println(" 이름은 비워둘 수 없습니다.")
        return
    }


    if len(country) < 2 {
        fmt.Println(" 국가 이름이 너무 짧습니다.")
        return
    }


    fmt.Printf(" 이름: %s, 국가: %s\n", name, country)
}




```
