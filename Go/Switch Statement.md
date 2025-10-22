# Switch Statement



```go
package main


import "fmt"


func main() {
    day := "Wednesday"


    switch day {
    case "Monday":
        fmt.Println("오늘은 월요일이에요!")
    case "Tuesday":
        fmt.Println("오늘은 화요일이에요!")
    case "Wednesday":
        fmt.Println("오늘은 수요일이에요!")
    default:
        fmt.Println("나머지 요일이에요!")
    }
}


```
