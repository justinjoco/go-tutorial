Sample code link: ([https://repl.it/@jjoco/go-pointers](https://repl.it/@jjoco/go-pointers))

Pointers essentially points to a place in memory that stores a variable of type T (ie memory address). This is similar to pointers used in C-like languages.

#### Regular vs. Short Assignment

One can define pointers via regular or short assigning, like any other variable. Dereferencing them is identical to that of other languages, eg if iPtr is a pointer, *iPtr dereferences it.

Regular
```go
var iPtr *int

i := 42
iPtr = &i

fmt.Println(*iPtr)
//Output = "42"
```
Short Assignment
```go
j := 24
jPtr := &j

fmt.Println(*jPtr)
// Output = "24"
```
### Pass by Value vs. Pass By Pointer

If you intend to change the input variable to a function and have the change be visible from the caller, use pointers.


#### Pass by Value
```go
//Doubles input 
func doubleByValue(x int) {
    x *= 2
}
```

```go
/*Pass By Value Call*/
k := 32
doubleByValue(k)
//Output = "After Pass By Value call: 32"  
```
#### Pass by Pointer 
```go
//Doubles input
func doubleByPointer(xPtr *int) {
    *xPtr *= 2
}
```
```go
/*Pass by Pointer Call*/
l := 32
doubleByPointer(&l)
//Output = "After Pass By Pointer call: 64" 
```
From the above, note that in the Pass By Value case, a copy of k is passed into doubleByValue, instead of k itself; as a result, the main function does not observe k changing.

However, in the Pass By Pointer case, the address of l is passed into doubleByPointer, which doubles the integer that is stored in that memory address. As a result, the main function observes l double.

### Pointers to Pointers

A developer can set a variable to be pointers to other pointers. For example, if I want to make a pointer to a pointer (double pointer), one can declare var doublePointer `**int`. It follows that one can declare a triple pointer (pointer to a double pointer) like var triplePointer `***int`, and so on and so forth.
