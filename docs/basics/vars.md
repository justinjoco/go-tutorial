Sample code link: [https://repl.it/@jjoco/go-variables-and-assignment](https://repl.it/@jjoco/go-variables-and-assignment)

#### Primitive Types

- Boolean: bool
- String: string
- Signed Integers: int, int8, int16, int32, int64
- Unsigned integers: uint, uint8, uint16, uint32, uint64
- Byte : byte => alias for uint8
- Rune: rune => alias for int32
- Floats: float32, float64
- Complex numbers: complex64, complex128
- **Void is not a type**

##### Note: int and uint are "are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit systems"

#### Regular Assignment

At compile time, the developer can specify the type of the variable declared using the var keyword. Compared with Typescript, Go only uses var, not let.

Typescript
```ts
let notAssignedInt : number

console.log("Not assigned int: ", notAssignedInt)

//Compile error => notAssignedInt is not assigned

let notAssignedVar

console.log("Not assigned var: ", notAssignedVar)

//Output = "Not assigned var: undefined"

let assignedBool1: boolean = true

console.log("AssignedBool: ", assignedBool1)

//Output = "AssignedBool: true"

let assignedBool2 = false

console.log("AssignedBool: ", assignedBool2)

//Output = "AssignedBool: false"
```
Go

```go
var notAssignedInt int

fmt.Printf("Not assigned int: %d\n", notAssignedInt) //%d decimal

//Output = "Not assigned int: 0"

var notAssignedVar

fmt.Println("Not assigned var: ", notAssignedVar)

//Compile error => type is not defined for "notAssignedVar"

var assignedBool1 bool = true

fmt.Printf("Assigned bool = %t\n", assignedBool1) //%t boolean value

//Output = "Assigned bool = true"

var assignedBool2 = false

fmt.Printf("Assigned bool = %t\n", assignedBool2) //%t boolean value

//Output = "Assigned bool = false"
```

- Notes
  - Only var is used when creating a new variable
  - No colons when specifying a variable's type
  - Uninitialized variables are set to their default "zero" value:
    - Number types (eg ints, unsigned ints, floats, etc.) are set to 0
    - Boolean types are set to false
    - String types are set to empty strings ""

#### Short Assignment

Developers can directly assign a variable using :=, and the compiler will infer what type of variable it is based on what was assigned. This is similar to assigning in Python, where the developer can directly assign a literal to a variable.

Note: it may not be in good practice to use shorthand in industry when maintaining type safety, but it will be used in this tutorial for cogency.

Python
```python
shortAssignedString = "short"

print("Short assigned string: {}".format(shortAssignedString))

//Output = "Short assigned string: short"
```

Golang
```go
shortAssignedString := "short"

fmt.Printf("Short assigned string: %s\n",

shortAssignedString) //%s string

//Output= "Short assigned string: short"
```

#### Multiple Assignments

Similar to other languages, the developer can assign multiple variables at once using regular or short assigning.
```go
var multAssignedInt1, multAssignedInt2 = 3, 4

// Output: "multAssignedInt1 = 3, multAssignedInt2 = 4"

shortAssignedString1, shortAssignedString2 := "hello", "world"

// Output: "shortAssignedString1 = hello, shortAssignedString2 = world"
```
#### Constants

Constants can be assigned via const keyword, and camelCase is generally used as the naming convention; PascalCase when exporting a const.
```go
const ConstantNumber = 10

// Output = "Constant Number: 10"
```
Unfortunately, constants cannot be assigned via := short assignment syntax

#### Operators

Golang supports the same arithmetic, comparison, logical, bitwise, and assignment operators as other C-like languages. They are listed below.

##### Arithmetic

- `+` Addition
- `-` Subtraction
- `*` Multiplication
- `/` Divison
- `%` Modulus
- `++` Increment by 1
- `--` Decrement by 1

##### Comparison

- `<` Less than
- `>` Greater than
- `<=` Less than or equal to
- `>=` Greater than or equal to
- `==` Equal to
- `!=` Not equal to

##### Logical

- `&&` Conditional AND
- `||` Conditional OR
- `!` NOT

##### Assignment

- `+=` add, then assign
- `-=` subtract, then assign
- `*=` multiply, then assign
- `/=` divide, then assign
- `%=` modulo, then assign

##### Bitwise

- `&` Bitwise AND
- `|` Bitwise OR
- `^` Bitwise XOR
- `<<` Left shift
- `>>` Right shift