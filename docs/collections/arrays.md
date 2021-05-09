### Arrays: Fixed-Sized ([https://repl.it/@jjoco/go-arrays](https://repl.it/@jjoco/go-arrays))

Arrays in Go are similar to those in C-like languages. They are of fixed size and have no specific methods to use on them.

Hence, they are not nearly as used as often as slices, which we will cover in the next section. But, if you want to use them, creating, reading, and writing to arrays are very similar to that in other languages.

##### Syntax:

//Initalized via regular assignment

var exampleArr [arrSize]elementType

//Modifying array element

exampleArr[index] = value

//Literal declared with short assignment

literalArr := [n]elementType {element1, element2, ..., elementN}

##### Example

var boolArr [2]bool

boolArr[0] = true

//boolArr == [true false]

floatArr := [4]float64 {1.23, 4.5, 6.78, 9.0}

//floatArr == [1.23 4.5 6.78 9]
