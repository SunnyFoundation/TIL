# Goroutines & Concurrency
* Basic
* Channel




## Basic
```go
package main


import (
    "fmt"
    "time"
)


func printNumbers() {
    for i := 1; i <= 5; i++ {
        fmt.Println("Number:", i)
        time.Sleep(500 * time.Millisecond) // 0.5초 대기
    }
}


func printLetters() {
    for _, c := range []string{"A", "B", "C", "D", "E"} {
        fmt.Println("Letter:", c)
        time.Sleep(500 * time.Millisecond)
    }
}


func main() {
    go printNumbers() // 새로운 고루틴에서 실행
    go printLetters() // 또 다른 고루틴에서 실행


    time.Sleep(3 * time.Second) // 메인 고루틴이 끝나지 않게 잠시 대기
    fmt.Println("Done!")
}


```






## Channel
```go
package main


import (
    "fmt"
    "time"
)


func worker(ch chan string) {
    fmt.Println("고루틴 시작!")
    time.Sleep(2 * time.Second)
    ch <- "Working Complete!" // 채널로 메시지 전송
}


func main() {
    ch := make(chan string) // 채널 생성


    go worker(ch) // 고루틴 실행


    fmt.Println("Waiting Message...")
    msg := <-ch // 채널로부터 메시지 수신 (blocking)
    fmt.Println("받은 메시지:", msg)
}


```
