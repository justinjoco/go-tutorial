Sample code link: ([https://repl.it/@jjoco/go-switch-case](https://repl.it/@jjoco/go-switch-case))

Like C-like langauges and TS, Go supports switch-case statements, configured with or without an expression to evaluate cases:

#### Switch with Expression

##### Syntax
```go
switch expression {

case x:

// Do in case x...

case y:

// Do in case y...

case z:

// Do in case z...

.

.

.

default:

//Do when no other case is satisfied ...

}
```
Syntax notes

- No break after each case
- No parentheses around expression

##### Example:
```go
color := "red"

switch color {

case "green":

fmt.Println("Go")

case "yellow":

fmt.Println("Slow")

default:

fmt.Println("Stop")

}

//Output = "Stop"
```
#### Switch used as a Long If-Else

Like switch(true) in other languages, using switch in Go without an expression can be used as a cleaner if-else statement, especially with many conditions.

##### Syntax

```go
switch {

case condition1:

...

case condition2:

...

case condition3:

...

.

.

.

default:

...

}
```
Syntax notes:

- No break after each case
- No true expression needed in switch

##### Go Example:
```go
grade := 71

letterGrade := ""

switch {

case grade > 90:

letterGrade = "A"

case grade > 80:

letterGrade = "B"

case grade > 70:

letterGrade = "C"

case grade > 65:

letterGrade = "D"

default:

letterGrade = "F"

}

fmt.Printf("Your grade is %s\n", letterGrade)

//Output = "Your grade is C"
```