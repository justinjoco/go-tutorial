### Functions ([https://repl.it/@jjoco/go-functions](https://repl.it/@jjoco/go-functions))

Go&#39;s function declaration uses the func keyword, and the dev can specify input and output parameter types.

##### Syntax

Typescript

function functionName(arg0: Arg1Type, ... ,

argN: ArgNType): ReturnType {

//Function code goes here...

}

Go

func functionName(arg0 Arg1Type, ... ,

argN ArgNType) ReturnType {

//Function code goes here...

}

- Compared to TS:
  - function =\&gt; func
  - No colons between variable name and its type

##### Example: Get hypotenuse of triangle given leg lengths

func getHypotenuse(x float64, y float64) float64 {

return math.Sqrt(math.Pow(x,2) + math.Pow(y,2))

}

// Output of getHypotenuse(3, 4) = 5

#### Defer

The defer keyword is used to run a statement after the current function has returned. You might want to use this if, for example, you had a port listener and you wanted to close it after a function returns.

##### Sample:

func testDefer(){

defer fmt.Println(&quot;Called after testDefer() returns&quot;)

fmt.Println(&quot;Called during testDefer() call&quot;)

}

//Output = &quot;Called during testDefer() call&quot;

// &quot;Called after testDefer() returns&quot;

#### Variadic Functions

You can define a function to have a variable amount of arguments (of the same type) like the following:

func sum(numbers ...int) int {

total := 0

for \_, number := range numbers {

total += number

}

return total

}

The above function can have two or more integers as parameters, and the function would work fine.

This allows functions like append to have a variable amount of elements to add into a slice.

In main function:

numbers := []int {1, 2, 3, 4, 5, 6}

fmt.Println(sum(numbers...))

// Output = &quot;21&quot;

- Use …elementType in function signature to denote a varying amount of arguments of elementType
- Use elementArr... to unpack the elements in elementArr into function&#39;s input
