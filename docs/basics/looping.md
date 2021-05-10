Sample code link: ([https://repl.it/@jjoco/go-looping](https://repl.it/@jjoco/go-looping))

#### Traditional For-Looping

Like many other languages, Go supports traditional for-looping. The caveat is the lack of parentheses around the for statements

Syntax
```go
for i := start ; i < end ; i += increment {
    //Do stuff each iteration
}
```
```go
factorial := 1
for i:=1 ; i <= 5 ; i++ {
    factorial *= i
}
//Output = "5! = 120"
```
#### "While" For-Loops

Unlike many other languages, Go does not have while loops; instead, for loops can be used to replace while loops by using the following syntax.

Syntax

```go
for condition {
    //Do stuff each iteration
}
```
- while (condition) => for condition with no parentheses around condition

Example:
```go
accumulator := 0
for accumulator < 10 {
    accumulator += 1
}
// Output = "Accumulator at end of while for-loop: 10"
```
#### Infinite Loops

Even though there are no while loops in Go, a developer can write infinite loops by using a for loop with no condition, like the following:

Syntax
```go
for {
    // Code that runs on each iteration goes here...
}
```
Example: Reads user input in terminal, forever
```go
//Imports "bufio" and "os" packages to parse and read user input in terminal
reader := bufio.NewReader(os.Stdin)
fmt.Printf("Testing Infinite Looping... \n")
fmt.Printf("-------------\n")
for {
    text, _ := reader.ReadString('\n')
    fmt.Printf("Text entered: %s\n", text)
}
```