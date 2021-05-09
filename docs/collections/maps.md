### Maps: Go&#39;s HashTables/HashMaps ([https://repl.it/@jjoco/go-maps](https://repl.it/@jjoco/go-maps))

Go implements map, a key-value data structure similar to Dictionaries in Python and Hashtables/HashMaps in Java.

#### Creating a Map

A dev can use literal-based syntax or the make function to allocate memory for a new map.

exampleMap := make(map[KeyType]ValueType)

//Functionally identical to using the make function

otherExampleMap := map[KeyType]ValueType{}

//Use interface{} if the ValueType can be anything

anyValueMap := make(map[string]interface{})

- KeyType must be a type that is comparable =\&gt; &quot;boolean, numeric, string, pointer, channel, and interface types, and structs or arrays that contain only those types&quot;
- ValueType can be of any type, including custom structs or other maps
  - use interface{} as your ValueType to have the map&#39;s valueType be of anything

#### Reading and Writing Map Elements

Like other languages, one can directly read, write, and delete values from Go maps.

//Setting Map Elements

cardMap[&quot;ace&quot;] = 1

cardMap[&quot;jack&quot;] = 11

cardMap[&quot;queen&quot;] = 12

cardMap[&quot;king&quot;] = 13

// cardMap == map[ace:1 jack:11 king:13 queen:12]

//Reading Map Element

j := cardMap[&quot;queen&quot;]

//j == 12

//Deleting Map Element

delete(cardMap, &quot;king&quot;)

////cardMap == map[ace:1 jack:11 queen:12]

- delete(map, key) =\&gt; deletes key-value pair in map whose key is key

#### Map Literals

Use map literals to define the initial elements in a map.

trafficLightMap := map[string]string{

&quot;red&quot;: &quot;stop&quot;,

&quot;green&quot;: &quot;go&quot;,

&quot;yellow&quot;: &quot;slow&quot;,

}

#### Iterating Through Maps

Similar in syntax to slice iteration, a dev can use range to iterate through the key-value pairs in a map.

for key, value := range exampleMap{

//... Process key and/or value

}

- Can use \_ in place of key or value if they aren&#39;t needed

Example:

Go code

for key, value := range cardMap{

fmt.Println(&quot;Key:&quot;, key, &quot;; Value:&quot;, value)

}

Console output

Key: ace ; Value: 1

Key: jack ; Value: 11

Key: queen ; Value: 12

#### Getting a Key&#39;s Value if the pair exists

There is an optional second return value when reading from a map that tells the dev if a key-value pair exists.

##### Syntax

value, ok := someMap[key]

if !ok{

//Do something if there is no key-value pair

}

##### Checking for key-value existence

If you don&#39;t care for retrieving the value, one can just check the existence of the key-value pair.

\_, ok := someMap[key]

if !ok{

//Do something if there is no key-value pair

}

##### Example:

//Given: &quot;king&quot; and its value don&#39;t exist in cardMap

k, ok := cardMap[&quot;king&quot;]

if !ok{

fmt.Println(&quot;king isn&#39;t there&quot;)

}

//Output = &quot;king isn&#39;t there&quot;