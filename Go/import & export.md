# import & export
* export
* import



## export
```go
package mathutils


// Add 함수는 두 숫자를 더함
func Add(a, b int) int {
    return a + b
}



함수를 외부로 꺼내려면 대문자를 사용해야함
```




## import
```go
package main


import (
    "GO/greet"
    "GO/mathutils"
    "fmt"
)


func main() {
    fmt.Println(greet.Hello("Sun"))
    fmt.Println("2 + 3 =", mathutils.Add(2, 3))
}





함수를 외부로 꺼내려면 대문자를 사용해야함
```
