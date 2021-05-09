### Variables and Assignment ([https://repl.it/@jjoco/go-variables-and-assignment](https://repl.it/@jjoco/go-variables-and-assignment))

#### Primitive Types

- Boolean: bool
- String: string
- Signed Integers: int, int8, int16, int32, int64
- Unsigned integers: uint, uint8, uint16, uint32, uint64
- Byte : byte =\&gt; alias for uint8
- Rune: rune =\&gt; alias for int32
- Floats: float32, float64
- Complex numbers: complex64, complex128
- **Void is not a type**

##### Note: int and uint are &quot;are usually 32 bits wide on 32-bit systems and 64 bits wide on 64-bit systems&quot;

#### Regular Assignment

At compile time, the developer can specify the type of the variable declared using the var keyword. Compared with Typescript, Go only uses var, not let.

Typescript

let notAssignedInt : number

console.log(&quot;Not assigned int: &quot;, notAssignedInt)

//Compile error =\&gt; notAssignedInt is not assigned

let notAssignedVar

console.log(&quot;Not assigned var: &quot;, notAssignedVar)

//Output = &quot;Not assigned var: undefined&quot;

let assignedBool1: boolean = true

console.log(&quot;AssignedBool: &quot;, assignedBool1)

//Output = &quot;AssignedBool: true&quot;

let assignedBool2 = false

console.log(&quot;AssignedBool: &quot;, assignedBool2)

//Output = &quot;AssignedBool: false&quot;

Go

var notAssignedInt int

fmt.Printf(&quot;Not assigned int: %d\n&quot;, notAssignedInt) //%d decimal

//Output = &quot;Not assigned int: 0&quot;

var notAssignedVar

fmt.Println(&quot;Not assigned var: &quot;, notAssignedVar)

//Compile error =\&gt; type is not defined for &quot;notAssignedVar&quot;

var assignedBool1 bool = true

fmt.Printf(&quot;Assigned bool = %t\n&quot;, assignedBool1) //%t boolean value

//Output = &quot;Assigned bool = true&quot;

var assignedBool2 = false

fmt.Printf(&quot;Assigned bool = %t\n&quot;, assignedBool2) //%t boolean value

//Output = &quot;Assigned bool = false&quot;

- Notes
  - Only var is used when creating a new variable
  - No colons when specifying a variable&#39;s type
  - Uninitialized variables are set to their default &quot;zero&quot; value:
    - Number types (eg ints, unsigned ints, floats, etc.) are set to 0
    - Boolean types are set to false
    - String types are set to empty strings &quot;&quot;

#### Short Assignment

Developers can directly assign a variable using :=, and the compiler will infer what type of variable it is based on what was assigned. This is similar to assigning in Python, where the developer can directly assign a literal to a variable.

Note: it may not be in good practice to use shorthand in industry when maintaining type safety, but it will be used in this tutorial for cogency.

Python

shortAssignedString = &quot;short&quot;

print(&quot;Short assigned string: {}&quot;

.format(shortAssignedString))

//Output = &quot;Short assigned string: short&quot;

Golang

shortAssignedString := &quot;short&quot;

fmt.Printf(&quot;Short assigned string: %s\n&quot;,

shortAssignedString) //%s string

//Output= &quot;Short assigned string: short&quot;

#### Multiple Assignments

Similar to other languages, the developer can assign multiple variables at once using regular or short assigning.

var multAssignedInt1, multAssignedInt2 = 3, 4

// Output: &quot;multAssignedInt1 = 3, multAssignedInt2 = 4&quot;

shortAssignedString1, shortAssignedString2 := &quot;hello&quot;, &quot;world&quot;

// Output: &quot;shortAssignedString1 = hello, shortAssignedString2 = world&quot;

#### Constants

Constants can be assigned via const keyword, and camelCase is generally used as the naming convention; PascalCase when exporting a const.

const ConstantNumber = 10

// Output = &quot;Constant Number: 10&quot;

Unfortunately, constants cannot be assigned via := short assignment syntax

#### Operators

Golang supports the same arithmetic, comparison, logical, bitwise, and assignment operators as other C-like languages. They are listed below.

##### Arithmetic

- + Addition
- - Subtraction
- \* Multiplication
- /Divison
- % Modulus
- ++ Increment by 1
- -- Decrement by 1

##### Comparison

- \&lt; Less than
- \&gt; Greater than
- \&lt;= Less than or equal to
- \&gt;= Greater than or equal to
- == Equal to
- != Not equal to

##### Logical

- &amp;&amp; Conditional AND
- || Conditional OR
- ! NOT

##### Assignment

- += add, then assign
- -= subtract, then assign
- \*= multiply, then assign
- /= divide, then assign
- %= modulo, then assign

##### Bitwise

- &amp; Bitwise AND
- | Bitwise OR
- ^ Bitwise XOR
- \&lt;\&lt; Left shift
- \&gt;\&gt; Right shift