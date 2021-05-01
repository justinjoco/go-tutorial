1. Download Go from https://golang.org/
2. Create a source code directory and input your Go code in there, with extension .go
3. Ways to run code
    1. Running one Go file: two ways
        - Use go build `<filename>` then run `./<filename>` to run Go executable
        - Use go run `<filename>` to build and run code in one command
    2. Running a Go source directory
        1. Be in the directory one above the Go source directory
        2. Run `go build -o <output-executable> <source-directory>`, in which `<output-exectuable>` is your custom name of the Go executable
        3. Run `./<output-executable> <args>`, in which `<args>` are potential input arguments to executable

### Hello World ([https://repl.it/@jjoco/go-hello-world](https://repl.it/@jjoco/go-hello-world))

- Need a main function to run Go program, like other C-like languages

**Note**

1. The first statement in a Go source file must be package name. Executable commands must always use package main.
2. Use fmt package in order to print out strings to the console
  - fmt.Println() =\&gt; prints a list of variables to STDOUT with default formatting and inserts spaces between the variables  **and**  appends a new line at the end.
  - fmt.Printf() =\&gt;allows you to specify the formatting using a format template