### Conditionals ([https://repl.it/@jjoco/go-conditionals](https://repl.it/@jjoco/go-conditionals))

#### Traditional If, Else-If, Else Statements

Like all other programming languages, Go has traditional if-else statements; the main difference is the lack of parentheses around the condition:

##### Syntax

Typescript:

if (condition) {

//Do stuff in first condition ...

} else if (otherCondition) {

//Do stuff in otherCondition...

} else {

//Do stuff if none of the above is satisfied ...

}

Go:

if condition {

//Do stuff in first condition ...

} else if otherCondition {

//Do stuff in otherCondition...

} else {

//Do stuff if none of the above is satisfied ...

}

##### Go example:

count := 6

if count \&lt; 10 {

fmt.Printf(&quot;Count is below 10 at value %d\n&quot;, count)

}

// Output = &quot;Count is below 10 at value 6&quot;

count = 51

if count %2 == 0 {

fmt.Printf(&quot;Count is even!\n&quot;)

} else {

fmt.Printf(&quot;Count is odd!\n&quot;)

}

//Output = &quot;Count is odd!&quot;

count = 25

if count %15 == 0 {

fmt.Printf(&quot;FizzBuzz\n&quot;)

} else if count % 5 == 0 {

fmt.Printf(&quot;Buzz\n&quot;)

} else if count % 3 == 0 {

fmt.Printf(&quot;Fizz\n&quot;)

} else {

fmt.Printf(&quot;NoneOfTheAbove\n&quot;)

}

//Output = &quot;Buzz&quot;

#### If with Short Assignment

In Go, the user can assign a variable and condition on that variable on the same line (separated by a ;), like the following

if shortStatementInt := 32; shortStatementInt \&gt; 30{

fmt.Printf(&quot;shortStatementInt is above 30!\n&quot;)

}

//Output = &quot;shortStatementInt is above 30!&quot;

In the above example, shortStatementInt is assigned, then evaluated in the condition following the ;