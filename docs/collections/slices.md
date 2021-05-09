### Slices: Dynamically-Sized Arrays [https://repl.it/@jjoco/go-slices](https://repl.it/@jjoco/go-slices)

Slices are essentially dynamic arrays that have several useful methods and offer flexibility that arrays do not. Thus, slices are used much more often than arrays.

##### Slice internal structure

If we take a look into a slice&#39;s internals, it contains a pointer to an actual array, and the length and capacity fields relevant to the internal array. In perspective, slices are wrappers of fixed-arrays that dynamically change the properties of their internal arrays.

![](RackMultipart20210429-4-9wxods_html_413b63491413af40.png)

#### Creating a New, Empty Slice

One can create a slice similar to creating an array, but you don&#39;t specify the size at compile-time:

var slice0 []int

// slice0 == nil

slice1 := []int{}

// slice1 == []

//This is functionally identical to slice1&#39;s declaration

slice2 := make([]int, 0)

// slice2 == []

Use make([]elementType, len, cap) to create a slice that contains elements of type elementType whose internal array&#39;s first len elements are memory-allocated

- cap is an optional parameter that denotes the internal array&#39;s initial allocated size; cap == len if cap is not specified

#### Slice Literals

One can declare a slice and specifically define its elements.

strLiteralSlice := []string {&quot;this&quot;, &quot;is&quot;, &quot;a&quot;, &quot;test&quot;}

// strLiteralSlice = [this is a test]

#### Reading and Writing Slice Elements

Reading and writing slice elements is similar to doing so to arrays.

//Setting Element

strLiteralSlice[3] = &quot;shoe&quot;

// strLiteralSlice = [this is a shoe]

//Reading Element

j := strLiteralSlice[2]

// j == &quot;a&quot;

#### Slice Methods

Slices have useful methods that a dev can use

len(slice) =\&gt; Returns length (integer) of slice

cap(slice) =\&gt; returns capacity (integer) of slice

append(slice, newElements…) =\&gt; returns a slice that contains elements from newElements added into input slice

##### Append example:

appendSlice := []int{3, 4, 1}

//&quot;Before Appending [3 4 1]&quot;

appendSlice = append(appendSlice, 23, 21, 43)

appendSlice = append(appendSlice, []int{3,2,1}...)

//&quot;After Appending [3 4 1 23 21 43 3 2 1]&quot;

Notes

- To accumulate a slice, be mindful to have the slice be the input and output to the append function
- … succeeding a slice represents unpacking the elements in that slice into arguments for the function

copy(destSlice, srcSlice) =\&gt; copies elements from srcSlice into destSlice; returns nothing

##### Copy example:

origSlice := []int{4,3,2}

copySlice := make([]int, len(origSlice))

copy(copySlice, origSlice)

//&quot;Original Slice : [4 3 2] ; Copy Slice : [4 3 2]&quot;&quot;

#### Iterating through a Slice

You can certainly iterate through an slice like in other languages by using the slice&#39;s indices. However, one can use the range keyword to iterate through a slice&#39;s indices and elements simultaneously without using traditional array. This is very similar to using the enumerate function in Python.

Typescript

//Iterate via indexes

for (let i = 0; i \&lt; N ; i++){

Do stuff to exampleArr[i]

}

//Iterate via for...of

for (const element of exampleArr){

Do stuff to element

}

Go

// element == exampleSlice[i]

for index, element := range exampleSlice {

Do stuff with index or element

}

Example:

Go code

iterSlice := []string{&quot;baseball&quot;, &quot;basketball&quot;, &quot;soccer&quot;, &quot;hockey&quot;, &quot;football&quot;}

//Use if both index and element are needed

for index, element := range iterSlice {

fmt.Println(&quot;index = &quot;, index)

fmt.Println(&quot;element = &quot;, element)

}

//Next two loops are the same, essentially

//Use if knowing the element value is not needed

for index, \_ := range iterSlice {

fmt.Println(&quot;index = &quot;, index)

}

for index := range iterSlice {

fmt.Println(&quot;index = &quot;, index)

}

//Use the index is not needed

for \_, element := range iterSlice {

fmt.Println(&quot;element = &quot;, element)

}

Console output

index = 0

element = baseball

index = 1

element = basketball

index = 2

element = soccer

index = 3

element = hockey

index = 4

element = football

index = 0

index = 1

index = 2

index = 3

index = 4

index = 0

index = 1

index = 2

index = 3

index = 4

element = baseball

element = basketball

element = soccer

element = hockey

element = football

- Use \_ in place of index or element for whichever is not needed

#### Creating a Slice from an Array or Slice

A slice can be created from a previously created array or index by using the following syntax. The slicing syntax is very similar to that of getting list elements via range indices in Python.

##### Syntax

- exampleArrOrSlice[:end] =\&gt; gets a slice of elements from beginning of exampleArrOrSlice until indexend (excluding element at index end)
- exampleArrOrSlice[start:] =\&gt; gets a slice of elements starting from index start (inclusive) until the end of exampleArrOrSlice
- exampleArrOrSlice[start:end] =\&gt; gets a slice of elements from exampleArrOrSlice starting from index start (inclusive) until the end index end(exclusive)

Example:

intSlice := []int{1, 2, 3, 4, 5, 6}

beginIntSlice := intSlice[:2]

middleIntSlice := intSlice[2:4]

endIntSlice := intSlice[4:]

// beginIntSlice == [1 2]

// middleIntSlice == [3 4]

// endIntSlice == [5 6]