# Conditional 

* if / else
* Declare Variable


## if / else
```go
package main


import "fmt"


func main() {
    score := 100


    if score >= 90 {
        fmt.Println("A 학점")
    } else if score >= 80 {
        fmt.Println("B 학점")
    } else if score >= 70 {
        fmt.Println("C 학점")
    } else {
        fmt.Println("F 학점")
    }


}


```



## Declare Variable
```go
if n := 10; n%2 == 0 {
    fmt.Println(n, "은 짝수입니다.")
} else {
    fmt.Println(n, "은 홀수입니다.")
}




```
