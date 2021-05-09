Sample code link: ([https://repl.it/@jjoco/go-conditionals](https://repl.it/@jjoco/go-conditionals))

#### Traditional If, Else-If, Else Statements

Like all other programming languages, Go has traditional if-else statements; the main difference is the lack of parentheses around the condition:

##### Syntax
```go
if condition {

//Do stuff in first condition ...

} else if otherCondition {

//Do stuff in otherCondition...

} else {

//Do stuff if none of the above is satisfied ...

}
```
##### Go example:
```go
count := 6

if count < 10 {

fmt.Printf("Count is below 10 at value %d\n", count)

}

// Output = "Count is below 10 at value 6"

count = 51

if count %2 == 0 {

fmt.Printf("Count is even!\n")

} else {

fmt.Printf("Count is odd!\n")

}

//Output = "Count is odd!"

count = 25

if count %15 == 0 {

fmt.Printf("FizzBuzz\n")

} else if count % 5 == 0 {

fmt.Printf("Buzz\n")

} else if count % 3 == 0 {

fmt.Printf("Fizz\n")

} else {

fmt.Printf("NoneOfTheAbove\n")

}

//Output = "Buzz"
```
#### If with Short Assignment

In Go, the user can assign a variable and condition on that variable on the same line (separated by a ;), like the following
```go
if shortStatementInt := 32; shortStatementInt > 30{

fmt.Printf("shortStatementInt is above 30!\n")

}
//Output = "shortStatementInt is above 30!"
```
In the above example, shortStatementInt is assigned, then evaluated in the condition following the `;`