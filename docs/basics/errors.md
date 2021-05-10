Sample code link: ([https://repl.it/@jjoco/go-error-handling](https://repl.it/@jjoco/go-error-handling))

Some functions return an error type
```go
sampleVar, err := canReturnErrorFct(args)
if err != nil {
    //Do something if there's an error
}
```
If the function is successful, err would be nil.

Example
```go
sampleStr := "ffgds"
strToInt, err := strconv.Atoi(sampleStr)

if err != nil {
    log.Fatal(err)
}

fmt.Println(strToInt)
// Output = "2020/10/22 19:39:38 strconv.Atoi: parsing "ffgds": invalid syntax"
// "exit status 1"
```
**Ignoring errors**

If you're feeling ambitious, you can certainly skip error handling of a function like below using `_`:
```go
sampleVar, _ := canReturnErrorFct(args)
```
However, only do this if you're really confident that the function will not return an error ever