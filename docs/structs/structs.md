### [https://repl.it/@jjoco/go-structs](https://repl.it/@jjoco/go-structs)

Structs are analogous to classes in OOP languages. These are your user-defined types with their own fields.

#### Declaring a Struct

Use type and struct to declare a blueprint of your struct.

Typescript
```Typescript
/\*Creating a new Type\*/

type TypeName = {

field1: field1Type

field2: field2Type

.

.

.

}

/\*Creating a new Class\*/

class ClassName {

field1: Field1Type

.

.

.

constructor(args){

...

}

.

.

.

}
```
Go
```Go
type TypeName struct {

field1 field1Type

field2 field2Type

.

.

.

}
```
- Compared to TS:
  - Use of struct keyword instead of = when making a new type
  - No classes or objects in Go
  - No colon between field name and its type

 **Can declare outside calling file**

Fortunately, one can declare a struct outside of a function that declares one without any extra import syntax, as long as they fall under the same package.

```Go
/\*Declared in shape.go\*/

package main

type Rectangle struct{

width int

height int

}

type Circle struct {

radius float64

}
```
#### Using a Struct

Similar to creating a new class instance in OOP languages, a dev can create a new variable of your customized struct without extra keywords.

##### Syntax

Typescript
```ts
/\*Creating variable of new type\*/

let typeVar TypeName = {field1: field1Value , ..., fieldN: fieldNValue}

/\*Creating instance of custom class\*/

let classInstance1: ClassObj = new ClassObj(args)

let classInstance2 = new ClassObj(args)
```
Go
```go
/\*Declaring new type variable\*/

var structDefault StructName

var structCustom1 StructName = StructName{args}

var structCustom2 = StructName{args}

/\*Short Assignment\*/

structShort := StructName{args}
```
- Compared to TS:
  - No use of new keyword
  - Use of curly brackets {} instead of parentheses ()
  - No colons when declaring type
  - Fields within struct variable are initialized to their zero values without explicit assigning

Examples:

##### No input parameters

Fields within structs are zero-valued, if not defined at compile-time.

defaultRect := Rectangle{}

//Output = &quot;Rectangle object: {0 0}&quot;

// &quot;Width = 0; Height = 0&quot;

##### With input parameters

customRect := Rectangle{2, 4}

// Output = &quot;Rectangle object: {2 4}&quot;

// &quot;Width = 2; Height = 4&quot;

##### With input parameters specifically defined

customRect2 := Rectangle{height: 2, width: 4}

// Output = &quot;Rectangle object: {4 2}&quot;

// &quot;Width = 4; Height = 2&quot;

##### Using struct not defined in calling file

defaultCircle := Circle{}

//Output = &quot;Circle Object: {0}&quot;

// &quot;Radius = 0.000000&quot;

customCircle := Circle{4}

//Output = &quot;Circle Object: {4}&quot;

// &quot;Radius = 4.000000&quot;

##### Pointers and Structs

A dev can use a struct pointer similarly to any other pointer. They function similarly as well, as shown in the following Pass by Value and Pass by Pointer comparison.

| **Pass By Value** | **Pass By Pointer** |
| --- | --- |
| /\*Changes input rectangle&#39;s dimensions to specified dimensions\*/func changeRectByValue(rect Rectangle, width int, height int){rect.width = widthrect.height = height}Main:/\*Pass By Value Call\*/defaultRect = Rectangle{}changeRectByValue(defaultRect, 3, 4)//Output = &quot;Default Rect after change by value {0 0}&quot; | /\*Changes input rectangle&#39;s dimensions to specified dimensions\*/func changeRectByPointer(rectPtr \*Rectangle, width int, height int){(\*rectPtr).width = width(\*rectPtr).height = height}Main:/\*Pass by Pointer Call\*/defaultRect = Rectangle{}changeRectByPointer(&amp;defaultRect, 3, 4)//Output = &quot;Default Rect after change by pointer {3 4}&quot; |

### Methods ([https://repl.it/@jjoco/go-methods](https://repl.it/@jjoco/go-methods))

These are analogous to class methods in OOP languages

func (receiver ReceiverType) methodName(args) returnType{

...

}

Essentially, methods are functions that work for specific structs.

Let&#39;s say I have the following two structs defined.

type Coordinate struct {

x float64

y float64

}

type Vector struct{

start Coordinate

end Coordinate

}

The following function works for only Vector structs:

func (vec Vector) CalculateLength() float64 {

return math.Sqrt(math.Pow((vec.end.x - vec.start.x), 2) + math.Pow((vec.end.y

- vec.start.y),2))

}

In main, I can call the struct&#39;s method like calling class methods in other OOP languages via .functionName():

start := Coordinate{1 , 1}

end := Coordinate{7, 9}

vector := Vector{start, end}

//vector.CalculateLength() == &quot;10&quot;

#### Pointer Receivers

Let&#39;s say I want a method that directly changes the fields within my receiver. You would use pointer receiver syntax, like the following:

func (receiver \*ReceiverType) MethodName(args) returnType{

...

}

Unlike traditional pointer syntax, the dev does not have to dereference the input pointer in order to modify the input struct variable, eg:

func (vec \*Vector) SetStartEnd(start Coordinate, end Coordinate){

vec.start = start

vec.end = end

}

Main:

vector.SetStartEnd(Coordinate{3, 4}, Coordinate{0, 0})

//&quot;Vector Length = 5&quot;

According to several sources, &quot;In general, all methods on a given type should have either value or pointer receivers, but not a mixture of both.&quot;

So, if we modified the CalculateLength function from earlier:

func (vec \*Vector) CalculateLength() float64 {

return math.Sqrt(math.Pow((vec.end.x - vec.start.x), 2) + math.Pow((vec.end.y - vec.start.y),2))

}

**Keep in mind that not using pointer receiver syntax would make a copy of the input struct variable. Since we&#39;re using a pointer receiver, we&#39;re only using the struct variable&#39;s address, reducing potential time and memory overhead.**