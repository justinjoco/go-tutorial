Sample code link: ([https://repl.it/@jjoco/go-routines](https://repl.it/@jjoco/go-routines))

Go's concurrency features are one of its main selling points over its competitors. Reading and writing concurrent programs is very easy. The "threads" in Go "go routines", and these are lightweight threads with small memory overhead. For example, a machine can run thousands of threads at a time, but that same machine can run millions of go routines. In addition, there is no need to import an extraneous package since concurrency is a core, primitive feature of the languages.

Go routines are functions that run concurrently from whichever function calls it. These are somewhat analogous to threads of other languages, though each is implemented differently under the hood.

To starting a new goroutine, use the `go` keyword
```go
go functionName(args)
```
Example:
```go
func countFromStartToEnd(name string, start int, end int, incr int){
    for i := start ; i < end ; i += incr {
        fmt.Println(name, " i = ", i)
        time.Sleep(time.Millisecond)
    }
}
```
Main function:
```go
go countFromStartToEnd("Goroutine1", 0, 5, 1)
go countFromStartToEnd("Goroutine2", 0, 5, 1)
countFromStartToEnd("Main", 0, 5, 1)

time.Sleep(5*time.Second)
fmt.Println("Finished")

/*
Sample console output:
Main i = 0
Goroutine2 i = 0
Goroutine1 i = 0
Goroutine2 i = 1
Main i = 1
Goroutine1 i = 1
Main i = 2
Goroutine2 i = 2
Goroutine1 i = 2
Goroutine1 i = 3
Goroutine2 i = 3
Main i = 3
Goroutine1 i = 4
Goroutine2 i = 4
Main i = 4
Finished
*/
```
- Function calls without the go keyword will be ran in the current goroutine
