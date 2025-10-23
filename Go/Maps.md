# Maps



```go
package main


import "fmt"


func main() {
    // 1️⃣ map 생성
    scores := map[string]int{
        "Sunny": 90,
        "Jobs":  85,
        "Elon":  92,
    }


    // 2️⃣ 값 읽기
    fmt.Println(scores["Sunny"]) // 90


    // 3️⃣ 값 추가
    scores["zukerberg"] = 88


    // 4️⃣ 값 수정
    scores["Jobs"] = 95


    // 5️⃣ 값 삭제
    delete(scores, "Elon")


    // 6️⃣ key 존재 여부 확인
    val, ok := scores["Jobs"]
    if ok {
        fmt.Println("Jobs:", val)
    } else {
        fmt.Println("Jobs is not in the map")
    }


    // 7️⃣ 전체 출력
    fmt.Println(scores)
}


```
