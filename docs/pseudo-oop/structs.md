Sample code link: [https://repl.it/@jjoco/go-structs](https://repl.it/@jjoco/go-structs)

Structs are analogous to classes in OOP languages. These are your user-defined types with their own fields.

#### Declaring a Struct

Use type and struct to declare a blueprint of your struct.

Typescript
```ts
/*Creating a new Type*/

type TypeName = {

field1: field1Type

field2: field2Type

.

.

.

}
```
```ts
/*Creating a new Class*/

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
/*Declared in shape.go*/

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
/*Creating variable of new type*/

let typeVar TypeName = {field1: field1Value , ..., fieldN: fieldNValue}

/*Creating instance of custom class*/

let classInstance1: ClassObj = new ClassObj(args)

let classInstance2 = new ClassObj(args)
```
Go
```go
/*Declaring new type variable*/

var structDefault StructName

var structCustom1 StructName = StructName{args}

var structCustom2 = StructName{args}

/*Short Assignment*/

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
```go
defaultRect := Rectangle{}

//Output = "Rectangle object: {0 0}"

// "Width = 0; Height = 0"
```
##### With input parameters
```go
customRect := Rectangle{2, 4}

// Output = "Rectangle object: {2 4}"

// "Width = 2; Height = 4"
```
##### With input parameters specifically defined
```go
customRect2 := Rectangle{height: 2, width: 4}

// Output = "Rectangle object: {4 2}"

// "Width = 4; Height = 2"
```
##### Using struct not defined in calling file
```go
defaultCircle := Circle{}

//Output = "Circle Object: {0}"

// "Radius = 0.000000"

customCircle := Circle{4}

//Output = "Circle Object: {4}"

// "Radius = 4.000000"
```
##### Pointers and Structs

A dev can use a struct pointer similarly to any other pointer. They function similarly as well, as shown in the following Pass by Value and Pass by Pointer comparison.

**Pass By Value**  
```go
/*Changes input rectangle's dimensions to specified dimensions*/
func changeRectByValue(rect Rectangle, width int, height int){
  rect.width = width
  rect.height = height
}
```
```go
/*Pass By Value Call*/
defaultRect = Rectangle{}
changeRectByValue(defaultRect, 3, 4)
//Output = "Default Rect after change by value {0 0}" 
```

**Pass By Pointer** 
```go
 /*Changes input rectangle's dimensions to specified dimensions*/
 func changeRectByPointer(rectPtr *Rectangle, width int, height int){
   (*rectPtr).width = width
   (*rectPtr).height = height
  }
```
```go
/*Pass by Pointer Call*/
defaultRect = Rectangle{}
changeRectByPointer(&defaultRect, 3, 4)
//Output = "Default Rect after change by pointer {3 4}" 
```