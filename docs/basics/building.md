
### Building and Running Go Code 
To run Go code, you need to do the following:

1. Download Go from https://golang.org/
2. Create a source code directory and input your Go code in there, with extension `.go`
3. Ways to run code
    1. Running one Go file: two ways
        - Use `go build <filename>` then run `./<filename>` to run Go executable
        - Use `go run <filename>` to build and run code in one command
    2. Running a Go source directory
        1. Be in the directory one above the Go source directory
        2. Run `go build -o <output-executable> <source-directory>`, in which `<output-exectuable>` is your custom name of the Go executable
        3. Run `./<output-executable> <args>`, in which `<args>` are potential input arguments to executable

### Hello World 
Sample code link: ([https://repl.it/@jjoco/go-hello-world](https://repl.it/@jjoco/go-hello-world))

To create a "Hello World" program, you need a main function, like other C-like languages. Take the following example:
```Go
package main

import "fmt"

func main(){
    fmt.Println("Hello World")
}

```

**Notes**

- The first statement in a Go source file must be package name. Executable commands must always use package main.
- Use `fmt` package in order to print out strings to the console. Here are some important functions:
    - `fmt.Println(... args)` : prints a list of variables to STDOUT with default formatting and inserts spaces between the variables  **and**  appends a new line at the end.
    - `fmt.Printf(stringFormat, fields)` : allows you to specify the formatting using a format template