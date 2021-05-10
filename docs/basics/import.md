### Importing Packages

#### Importing One Package

- Only need a package name in quotes

```go
import "packageName"
```
#### Importing Multiple Packages

- Encapsulate packages in parentheses
- Separate packages by newline
```go
import (
    "package1"
    "package2"
    .
    .
    .
    "packageN"
)
```
#### Package Aliasing

- Can alias package names if the developer prefers not to use the package's full name

Python
```python
import module1 as alias1, module2 as alias2
```

Go
```go
import (
    alias1 "package1"
    alias2 "package2"
)
```
## Useful Packages

**General utility**

- `strconv` : converts numeric types (bools, ints, floats, etc.) and certain strings types to and from ASCII strings
- `fmt` : "implements formatted I/O with functions analogous to C's printf and scanf. The format 'verbs' are derived from C's but are simpler."
- `time` : "provides functionality for measuring and displaying time"
- `sync` "provides basic synchronization primitives such as mutual exclusion locks. "
- `strings` : "implements simple functions to manipulate UTF-8 encoded strings."

**Testing**

- `testing`: "provides support for automated testing of Go packages. It is intended to be used in concert with the `go test` command, which automates Go unit testing

- `github.com/stretchr/testify/suite` : "package provides [testing] functionality that you might be used to from more common object oriented languages. With it, you can build a testing suite as a struct, build setup/teardown methods and testing methods on your struct, and run them with 'go test' as per normal

**File I/O**

- `bufio`: ;implements buffered I/O. It wraps an io.Reader or io.Writer object, creating another object (Reader or Writer) that also implements the interface but provides buffering and some help for textual I/O."
- `os` : " provides a platform-independent interface to operating system functionality"

**Networking**

- `net` : "provides a portable interface for network I/O, including TCP/IP, UDP, domain name resolution, and Unix domain sockets"
- `net/http` : "provides HTTP client and server implementations."
- `github.com/gorilla/mux` : "implements a request router and dispatcher for matching incoming requests to their respective handler."
