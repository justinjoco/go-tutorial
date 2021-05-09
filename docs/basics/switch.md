### Switch-Case ([https://repl.it/@jjoco/go-switch-case](https://repl.it/@jjoco/go-switch-case))

Like C-like langauges and TS, Go supports switch-case statements, configured with or without an expression to evaluate cases:

#### Switch with Expression

##### Syntax

Typescript

switch (expression) {

case x:

// Do in case x...

break

case y:

// Do in case y...

break

case z:

// Do in case z...

break

.

.

.

default:

//Do when no other case is satisfied ...

}

Go

switch expression {

case x:

// Do in case x...

case y:

// Do in case y...

case z:

// Do in case z...

.

.

.

default:

//Do when no other case is satisfied ...

}

Syntax notes

- No break after each case
- No parentheses around expression

##### Example:

color := &quot;red&quot;

switch color {

case &quot;green&quot;:

fmt.Println(&quot;Go&quot;)

case &quot;yellow&quot;:

fmt.Println(&quot;Slow&quot;)

default:

fmt.Println(&quot;Stop&quot;)

}

//Output = &quot;Stop&quot;

#### Switch used as a Long If-Else

Like switch(true) in other languages, using switch in Go without an expression can be used as a cleaner if-else statement, especially with many conditions.

##### Syntax

Typescript

switch (true) {

case condition1:

...

break

case condition2:

...

break

case condition3:

...

break

.

.

.

default:

...

}

Golang

switch {

case condition1:

...

case condition2:

...

case condition3:

...

.

.

.

default:

...

}

Syntax notes:

- No break after each case
- No true expression needed in switch

##### Go Example:

grade := 71

letterGrade := &quot;&quot;

switch {

case grade \&gt; 90:

letterGrade = &quot;A&quot;

case grade \&gt; 80:

letterGrade = &quot;B&quot;

case grade \&gt; 70:

letterGrade = &quot;C&quot;

case grade \&gt; 65:

letterGrade = &quot;D&quot;

default:

letterGrade = &quot;F&quot;

}

fmt.Printf(&quot;Your grade is %s\n&quot;, letterGrade)

//Output = &quot;Your grade is C&quot;
