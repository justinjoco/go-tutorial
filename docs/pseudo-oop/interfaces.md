Sample code link: ([https://repl.it/@jjoco/go-interfaces](https://repl.it/@jjoco/go-interfaces))

Syntax

Interfaces are method blueprints and follow the syntax:
```go
type InterfaceName interface{

method1() returnType1

method2() returnType2

.

.

.

}
```
Example:

The following Shape interface defines two method signatures.
```go
type Shape interface{

getArea() float64

getDimensions() []float64

}
```
Structs can implement those method signatures, eg Rectangle and Circle.
```go
/*Rectangle Implements Shape methods*/

type Rectangle struct {

width float64

height float64

}

func (rect Rectangle) getArea() float64{

return rect.width * rect.height

}



func (rect Rectangle) getDimensions() []float64 {

return []float64 {rect.width, rect.height}

}
```
```go
/*Circle Implements Shape methods*/

type Circle struct {

radius float64

}

func (circle Circle) getArea() float64{

return math.Pi * math.Pow(circle.radius, 2)

}

func (circle Circle) getDimensions() []float64{

return []float64{circle.radius}

}
```
Though it's not immediately obvious, having these two structs define the Shape interface methods would be useful if a function's parameter is of the Shape interface.
```go
func PrintShapeArea(shape Shape){

fmt.Println("Shape Area = ", shape.getArea())

}

func PrintShapeDimensions(shape Shape){

fmt.Println("Shape Dimensions", shape.getDimensions())

}
```
So, instead of having a print function for each struct, there can be one print function that accepts the interface that each struct implements. This is for code cogency and to reduce redundant copy/paste code.
```go
rect := Rectangle{2 , 4}

circle := Circle{3}

PrintShapeDimensions(rect)

// "Shape Dimensions [2 4]"

PrintShapeDimensions(circle)

// "Shape Dimensions [3]"

PrintShapeArea(rect)

// "Shape Area = 8"

PrintShapeArea(circle)

// "Shape Area = 25"
```
Let's go through a more practical example. Let's say we have a black-box function that takes the io.Reader interface (from io package) as a parameter
```go
func handleReader(r io.Reader){

...

}
```
Structs that implement io.Reader must implement the Read(p []byte) (n int, err error) method, such as *os.File and *bytes.Buffer Since these structs have the Read method and the handleReader function only cares that the input struct implements the Read method, handleReader can handle both *os.File and *bytes.Buffer inputs without compilation error. Of course, there are many more structs that implement the io.Reader interface, and handleReader can handle inputs of each struct without compilation error.

#### Empty Interface

An empty interface contains zero methods. Since every type implements at least zero methods, the empty interface can be used as an "any" type, if the developer uncertain about the types of a function, map valueType, etc. For example, any map, slice, struct implement at least zero methods; thus, they implement the empty interface.

Examples:

##### Empty Interface as a ValueType
```go
sampleMap := make(map[string]interface{})

/*The next two pushes to the map are completely valid

since the ValueType is an empty interface*/

sampleMap["hello"] = "there"

sampleMap["brooklynn"] = 99

//sampleMap == map[brooklynn:99 hello:there]
```
In the above example, since strings and integers implement at least zero methods, they implement the empty interface, which allow each type to be added into sampleMap

##### Empty Interface as a function parameter type
```go
func printVariable(input interface{}){

fmt.Println(input)

}

// printVariable("hello") Output = "hello"

// printVariable(124553) Output = "124553"

// printVariable(1.034) Output = "1.034"
```
Similar to the reasoning above, since strings, floats, and integers have at least zero methods, they implement the empty interface, allowing each to be an input to the printVariable function.
