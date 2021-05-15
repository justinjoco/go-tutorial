
Sample code link: ([https://repl.it/@jjoco/go-methods](https://repl.it/@jjoco/go-methods))
### Writing and Using Methods
These are analogous to class methods in OOP languages
```go
func (receiver ReceiverType) methodName(args) returnType{
    //Do stuff here
}
```
Essentially, methods are functions that work for specific structs.

Let's say I have the following two structs defined.
```go
type Coordinate struct {
    x float64
    y float64
}
```
```go
type Vector struct{
    start Coordinate
    end Coordinate
}
```
The following function works for only Vector structs:
```go
func (vec Vector) CalculateLength() float64 {
    return math.Sqrt(math.Pow((vec.end.x - vec.start.x), 2) + math.Pow((vec.end.y- vec.start.y),2))
}
```
In main, I can call the struct's method like calling class methods in other OOP languages via `.functionName()`:
```go
start := Coordinate{1 , 1}
end := Coordinate{7, 9}
vector := Vector{start, end}
//vector.CalculateLength() == "10"
```
### Pointer Receivers

Let's say I want a method that directly changes the fields within my receiver. You would use pointer receiver syntax, like the following:
```go
func (receiver *ReceiverType) MethodName(args) returnType{
    //Do stuff here
}
```
Unlike traditional pointer syntax, the dev does not have to dereference the input pointer in order to modify the input struct variable, eg:
```go
func (vec *Vector) SetStartEnd(start Coordinate, end Coordinate){
    vec.start = start
    vec.end = end
}
```
Calling function:
```go
vector.SetStartEnd(Coordinate{3, 4}, Coordinate{0, 0})
//"Vector Length = 5"
```
According to several sources, "In general, all methods on a given type should have either value or pointer receivers, but not a mixture of both."

So, if we modified the CalculateLength function from earlier:
```go
func (vec *Vector) CalculateLength() float64 {
    return math.Sqrt(math.Pow((vec.end.x - vec.start.x), 2) + math.Pow((vec.end.y - vec.start.y),2))
}
```
Keep in mind that not using pointer receiver syntax would make a copy of the input struct variable. Since we're using a pointer receiver, we're only using the struct variable's address, reducing potential time and memory overhead.