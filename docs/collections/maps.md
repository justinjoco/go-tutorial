Sample code link: ([https://repl.it/@jjoco/go-maps](https://repl.it/@jjoco/go-maps))

Go implements map, a key-value data structure similar to Dictionaries in Python and Hashtables/HashMaps in Java.

#### Creating a Map

A dev can use literal-based syntax or the make function to allocate memory for a new map.
```go
exampleMap := make(map[KeyType]ValueType)

//Functionally identical to using the make function

otherExampleMap := map[KeyType]ValueType{}

//Use interface{} if the ValueType can be anything

anyValueMap := make(map[string]interface{})
```
- KeyType must be a type that is comparable => "boolean, numeric, string, pointer, channel, and interface types, and structs or arrays that contain only those types"
- ValueType can be of any type, including custom structs or other maps
  - use interface{} as your ValueType to have the map's valueType be of anything

#### Reading and Writing Map Elements

Like other languages, one can directly read, write, and delete values from Go maps.
```go
//Setting Map Elements

cardMap["ace"] = 1

cardMap["jack"] = 11

cardMap["queen"] = 12

cardMap["king"] = 13

// cardMap == map[ace:1 jack:11 king:13 queen:12]
```

Reading Map Element
```go
j := cardMap["queen"]

//j == 12
```
Deleting Map Element
```go
delete(cardMap, "king")

//cardMap == map[ace:1 jack:11 queen:12]
```
#### Map Literals

Use map literals to define the initial elements in a map.
```go
trafficLightMap := map[string]string{

"red": "stop",

"green": "go",

"yellow": "slow",

}
```
#### Iterating Through Maps

Similar in syntax to slice iteration, a dev can use range to iterate through the key-value pairs in a map.
```go
for key, value := range exampleMap{

//... Process key and/or value

}
```
- Can use `_` in place of key or value if they aren't needed

Example:

Go code
```go
for key, value := range cardMap{

fmt.Println("Key:", key, "; Value:", value)

}
/*
Console output
Key: ace ; Value: 1
Key: jack ; Value: 11
Key: queen ; Value: 12
*/
```
#### Getting a Key's Value if the pair exists

There is an optional second return value when reading from a map that tells the dev if a key-value pair exists.

Syntax
```go
value, ok := someMap[key]

if !ok{

//Do something if there is no key-value pair

}
```
##### Checking for key-value existence

If you don't care for retrieving the value, one can just check the existence of the key-value pair.
```go
_, ok := someMap[key]

if !ok{

//Do something if there is no key-value pair

}
```
##### Example:

//Given: "king" and its value don't exist in cardMap
```go
k, ok := cardMap["king"]

if !ok{

fmt.Println("king isn't there")

}

//Output = "king isn't there"
```