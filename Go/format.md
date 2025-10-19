# Format 

* %v
* %T
* Println
* Scanln



### %v
```go

package main
import "fmt"
func main() {
    var conferenceName = "Go Conference"
  
    fmt.Printf("Welcome to %v booking Applicaiton\n", conferenceName)

}

```



### %T
```go

package main
import "fmt"
func main() {

  
       var conferenceName = "Go Conference"

    fmt.Printf("conferenceName Type is  %T \n", conferenceName)


}



```





### Println
```go

package main
import "fmt"
func main() {

  
     var firstName string
    var lastName string
    var email string
    var userTickets uint


    // asking for user input
    fmt.Println("Enter Your First Name: ")
 


}



```



### Scanln
```go

package main
import "fmt"
func main() {

  
     var firstName string
    var lastName string
    var email string
    var userTickets uint


    // asking for user input
    fmt.Println("Enter Your First Name: ")
    fmt.Scanln(&firstName)



```
