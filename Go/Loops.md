# Loops
* Basic
* While
* Range



## Basic
```go
package main


import "fmt"


func main() {
    for i := 0; i < 5; i++ {
        fmt.Println("i =", i)
    }
}


```



## While
```go
package main


import "fmt"


func main() {
    count := 0
    for count < 3 {
        fmt.Println("count =", count)
        count++
    }


}



```





## Range
```go
package main


import "fmt"


func main() {
    nums := []int{10, 20, 30}


    for i, v := range nums {
        fmt.Println("index:", i, "value:", v)
    }


}




```
