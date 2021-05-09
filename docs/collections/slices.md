### Arrays: Fixed-Sized 
Sample code link: ([https://repl.it/@jjoco/go-arrays](https://repl.it/@jjoco/go-arrays))

Arrays in Go are similar to those in C-like languages. They are of fixed size and have no specific methods to use on them.

Hence, they are not nearly as used as often as slices, which we will cover in the next section. But, if you want to use them, creating, reading, and writing to arrays are very similar to that in other languages.

##### Syntax:
```go
//Initalized via regular assignment

var exampleArr [arrSize]elementType

//Modifying array element

exampleArr[index] = value

//Literal declared with short assignment

literalArr := [n]elementType {element1, element2, ..., elementN}
```
##### Example
```go
var boolArr [2]bool

boolArr[0] = true

//boolArr == [true false]

floatArr := [4]float64 {1.23, 4.5, 6.78, 9.0}

//floatArr == [1.23 4.5 6.78 9]
```
### Slices: Dynamically-Sized Arrays 
Sample code link: [https://repl.it/@jjoco/go-slices](https://repl.it/@jjoco/go-slices)

Slices are essentially dynamic arrays that have several useful methods and offer flexibility that arrays do not. Thus, slices are used much more often than arrays.

##### Slice internal structure

If we take a look into a slice's internals, it contains a pointer to an actual array, and the length and capacity fields relevant to the internal array. In perspective, slices are wrappers of fixed-arrays that dynamically change the properties of their internal arrays.

![](RackMultipart20210429-4-9wxods_html_413b63491413af40.png)

#### Creating a New, Empty Slice

One can create a slice similar to creating an array, but you don't specify the size at compile-time:
```go
var slice0 []int

// slice0 == nil

slice1 := []int{}

// slice1 == []

//This is functionally identical to slice1's declaration

slice2 := make([]int, 0)

// slice2 == []
```
Use `make([]elementType, len, cap)` to create a slice that contains elements of type elementType whose internal array's first len elements are memory-allocated

- cap is an optional parameter that denotes the internal array's initial allocated size; cap == len if cap is not specified

#### Slice Literals

One can declare a slice and specifically define its elements.
```go
strLiteralSlice := []string {"this", "is", "a", "test"}

// strLiteralSlice = [this is a test]
```
#### Reading and Writing Slice Elements

Reading and writing slice elements is similar to doing so to arrays.
```go
//Setting Element

strLiteralSlice[3] = "shoe"

// strLiteralSlice = [this is a shoe]

//Reading Element

j := strLiteralSlice[2]

// j == "a"
```
#### Slice Methods

Slices have useful methods that a dev can use

`len(slice)` => Returns length (integer) of slice

`cap(slice)` => returns capacity (integer) of slice

`append(slice, newElements...)` => returns a slice that contains elements from newElements added into input slice

##### Append example:
```go
appendSlice := []int{3, 4, 1}

//"Before Appending [3 4 1]"

appendSlice = append(appendSlice, 23, 21, 43)

appendSlice = append(appendSlice, []int{3,2,1}...)

//"After Appending [3 4 1 23 21 43 3 2 1]"
```
Notes

- To accumulate a slice, be mindful to have the slice be the input and output to the append function
- `...` succeeding a slice represents unpacking the elements in that slice into arguments for the function

`copy(destSlice, srcSlice)` => copies elements from srcSlice into destSlice; returns nothing

##### Copy example:
```go
origSlice := []int{4,3,2}

copySlice := make([]int, len(origSlice))

copy(copySlice, origSlice)

//"Original Slice : [4 3 2] ; Copy Slice : [4 3 2]""
```
#### Iterating through a Slice

You can certainly iterate through an slice like in other languages by using the slice's indices. However, one can use the range keyword to iterate through a slice's indices and elements simultaneously without using traditional array. This is very similar to using the enumerate function in Python.

```go
// element == exampleSlice[i]

for index, element := range exampleSlice {

Do stuff with index or element

}
```
Example:

Go code
```go
iterSlice := []string{"baseball", "basketball", "soccer", "hockey", "football"}

//Use if both index and element are needed

for index, element := range iterSlice {

fmt.Println("index = ", index)

fmt.Println("element = ", element)

}

//Next two loops are the same, essentially

//Use if knowing the element value is not needed

for index, _ := range iterSlice {

fmt.Println("index = ", index)

}

for index := range iterSlice {

fmt.Println("index = ", index)

}

//Use the index is not needed

for _, element := range iterSlice {

fmt.Println("element = ", element)

}
```

- Use `_` in place of index or element for whichever is not needed

#### Creating a Slice from an Array or Slice

A slice can be created from a previously created array or index by using the following syntax. The slicing syntax is very similar to that of getting list elements via range indices in Python.

##### Syntax

- `exampleArrOrSlice[:end]` => gets a slice of elements from beginning of exampleArrOrSlice until indexend (excluding element at index end)
- `exampleArrOrSlice[start:]` => gets a slice of elements starting from index start (inclusive) until the end of exampleArrOrSlice
- `exampleArrOrSlice[start:end]` => gets a slice of elements from exampleArrOrSlice starting from index start (inclusive) until the end index end(exclusive)

Example:
```go
intSlice := []int{1, 2, 3, 4, 5, 6}

beginIntSlice := intSlice[:2]

middleIntSlice := intSlice[2:4]

endIntSlice := intSlice[4:]

// beginIntSlice == [1 2]

// middleIntSlice == [3 4]

// endIntSlice == [5 6]
```