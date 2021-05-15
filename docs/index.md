This document is a how-to for developers on how to read and write Go code. Readers are assumed to know at least one or more coding languages. Through this document, developers should be able to read and write basic Go syntax and leverage some of Go’s pseudo-OOP and concurrency features to write non-trivial programs.

This document will also include links to repl.it, in which readers can run and change pre-existing Go code to further understand how to use it.

**Please leave your feedback here:** <https://forms.gle/zezZNmo7XGrq5xZZ6>.

**To raise an issue on Github for feature requests or bug fixes, go here:** <https://github.com/justinjoco/go-tutorial/issues>

## What is the Go (Golang) language?
Firstly, Go is a compiled programming language. To understand what this means, we must distinguish two times: compile time and run time. For a program to run, your code must be compiled (compile time), and the resulting executable should be ran (run time).

- Compile time: a “complier” translates your human-readable code into a machine-readable binary (or executable) file. 

- Run time: The binary file is executed (or ran) by the machine to run your code’s program. 

Secondly, Go is statically-typed, which means that your code’s variables' data types must be known at compile time. This is to promote type safety, a language feature that restricts the amount of unknown states of your application or program that could potentially lead to unwanted, erroneous behavior.

Compared to other languages, some say it is a “better version of C” because not only does Go generally perform very well in terms of speed and memory efficiency (similarly to other C languages), but it is also easy to read and write. In addition, Go has memory safety, garbage collection, and concurrency features not present in C. In fact, Go was developed by Google developers who didn’t like C++, which is one of the earliest, most popular extensions of C.

## What applications are written in Go, and which companies use it?
- Applications
    - Docker Community Edition, Compose-CLI, etc.
    - InfluxDB: monitors computer performance metrics
    - Kubernetes: orchestrates containers across multiple servers
- Companies
    - Google
    - Heroku
    - Dropbox
    - MongoDB
    - Netflix
    - Twitch 
    - Uber

## Why should I use Go?
- It has very good run-time performance, similar to that of C and C++
- It is designed to be readable like Python or JS
    - Its syntax is like combination of Python, TS, and C
    - Go's concurrent programs are very easy to write 
- It's very performant in networking and multiprocessing
    - Go routines can be thought of as super lightweight threads
    - It's easy to communicate between go routines via channels
- **It's advised to use Go when developing scalable, high-performance applications**

### What are some cons with using Go?
- There is no race condition safety; you need to use synchronization primitives (eg. sync package)
- Error handling is bare-bones
- No generics implementation yet
- Compile-time strictness can be annoying
- Not at lot of other in-built data structures besides arrays, slices, and maps

## Useful Links

- A Tour of Go: [https://tour.golang.org/welcome/1](https://tour.golang.org/welcome/1)

- Go by Example: [https://gobyexample.com/](https://gobyexample.com/)

- Repl.it IDE: [https://repl.it/](https://repl.it/)

- Golang Blog: [https://blog.golang.org/](https://blog.golang.org/)