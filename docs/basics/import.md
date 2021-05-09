### Importing Packages

#### Importing One Package

- Only need a package name in quotes

import &quot;packageName&quot;

#### Importing Multiple Packages

- Encapsulate packages in parentheses
- Separate packages by newline

import (

&quot;package1&quot;

&quot;package2&quot;

.

.

.

&quot;packageN&quot;

)

#### Package Aliasing

- Can alias package names if the developer prefers not to use the package&#39;s full name

Python

import module1 as alias1, module2 as alias2

Go

import (

alias1 &quot;package1&quot;

alias2 &quot;package2&quot;

)

## Useful Packages

### General utility:

- strconv : converts numeric types (bools, ints, floats, etc.) and certain strings types to and from ASCII strings
- fmt : &quot;implements formatted I/O with functions analogous to C&#39;s printf and scanf. The format &#39;verbs&#39; are derived from C&#39;s but are simpler.&quot;
- time : &quot;provides functionality for measuring and displaying time&quot;
- sync &quot;provides basic synchronization primitives such as mutual exclusion locks. &quot;
- strings : &quot;implements simple functions to manipulate UTF-8 encoded strings.&quot;

### Testing

- testing: &quot;provides support for automated testing of Go packages. It is intended to be used in concert with the &quot;go test&quot; command, which automates execution of any function of the form

func TestXxx(\*testing.T)

where Xxx does not start with a lowercase letter. The function name serves to identify the test routine.&quot;

- github.com/stretchr/testify/suite : &quot;package provides [testing] functionality that you might be used to from more common object oriented languages. With it, you can build a testing suite as a struct, build setup/teardown methods and testing methods on your struct, and run them with &#39;go test&#39; as per normal

### File I/O

- bufio: &quot;implements buffered I/O. It wraps an io.Reader or io.Writer object, creating another object (Reader or Writer) that also implements the interface but provides buffering and some help for textual I/O.&quot;
- os : &quot; provides a platform-independent interface to operating system functionality&quot;

### Networking

- net : &quot;provides a portable interface for network I/O, including TCP/IP, UDP, domain name resolution, and Unix domain sockets&quot;
- net/http : &quot;provides HTTP client and server implementations.&quot;
- github.com/gorilla/mux : &quot;implements a request router and dispatcher for matching incoming requests to their respective handler.&quot;
