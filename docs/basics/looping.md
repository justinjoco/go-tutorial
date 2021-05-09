### Looping ([https://repl.it/@jjoco/go-looping](https://repl.it/@jjoco/go-looping))

#### Traditional For-Looping

Like many other languages, Go supports traditional for-looping. The caveat is the lack of parentheses around the for statements

Syntax

Typescript

for (let i = start; i \&lt; end; i+=increment ){

//Do stuff each iteration

}

Golang

for i := start ; i \&lt; end ; i += increment {

//Do stuff each iteration

}

Go example:

factorial := 1

for i:=1 ; i \&lt;= 5 ; i++ {

factorial \*= i

}

//Output = &quot;5! = 120&quot;

#### &quot;While&quot; For-Loops

Unlike many other languages, Go does not have while loops; instead, for loops can be used to replace while loops by using the following syntax.

Syntax

Typescript

while (condition){

//Do stuff each iteration

}

Go

for condition {

//Do stuff each iteration

}

- while (condition) =\&gt; for condition with no parentheses around condition

Example:

accumulator := 0

for accumulator \&lt; 10 {

accumulator += 1

}

// Output = &quot;Accumulator at end of while for-loop: 10&quot;

#### Infinite Loops

Even though there are no while loops in Go, a developer can write infinite loops by using a for loop with no condition, like the following:

##### Syntax

Typescript

while (true){

//Code that runs on each iteration goes here...

}

Go

for {

// Code that runs on each iteration goes here...

}

- while(true) =\&gt; for

##### Example: Reads user input in terminal, forever

//Imports &quot;bufio&quot; and &quot;os&quot; packages to parse and read user input in terminal

reader := bufio.NewReader(os.Stdin)

fmt.Printf(&quot;Testing Infinite Looping... \n&quot;)

fmt.Printf(&quot;-------------\n&quot;)

for {

text, \_ := reader.ReadString(&#39;\n&#39;)

fmt.Printf(&quot;Text entered: %s\n&quot;, text)

}