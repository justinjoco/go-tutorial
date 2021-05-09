Sample code link: ([https://repl.it/@jjoco/go-channels](https://repl.it/@jjoco/go-channels))

Go channels is the method of communication that allows go routines to talk to each other. These are FIFO. The dev has to define the type that goes into the channel. The type can be anything: structs, maps, slices, primitives, etc.

If two go routines were processes, the go channel is the bridge between them:


#### Non-Buffered Channels

By default channels are _unbuffered_, meaning that they will only accept sends (chan <-) if there is a corresponding receive (<- chan) ready to receive the sent value

Syntax:
```go
channel := make(chan ElementType)
```
#### Buffered Channels

_Buffered channels_ accept a limited number of values without a corresponding receiver for those values. These are much more flexible than unbuffered channels.
```go
channel := make(chan ElementType, channelSize)
```
#### Reading and Writing to Channels

The `<-` denotes which way a value is getting written into

##### Writing
```go
channel <- writeValue
```
- writeValue is getting written into channel

##### Reading
```go
readVar <- channel
```
- The front of channel is getting read into declared variable readVar

**Non-buffered example**

- A go routine is writing into nonBufferedChannel and has a receive in the main goroutine
```go
nonBuffedChannel := make(chan string)

go func(){

nonBuffedChannel <- "ping"

}()

fmt.Println(<-nonBuffedChannel)

fmt.Println("Finished")

This will not work:

messages := make(chan string)

messages <- "no"

fmt.Println(<-messages)

fmt.Println("Done")
```
This will not run correctly because there is no immediate receiver (eg a concurrent receiver) for the send into messages

**Buffered examples**
```go
messages := make(chan string, 2)

messages <- "hello there"

messages <- "general kenobi!!"

fmt.Println(<-messages)

fmt.Println(<-messages)
```
- Strings are getting written into the messages channel and read out in a FIFO way

#### Uni-directional Channels

A function can be configured to be able to only read from a given channel or be forced to only write into a channel. This is used for type safety, and it ensures no two go routines can write to the same channel.

**Send-Only**
```go
func functionName(sendOnlyChannel chan<- ElementType, ... ){

//This function can only write into the given channel

}
```
- The above function can only write data into sendOnlyChannel; it cannot read from the channel

**Receive-Only**
```go
func functionName(receiveOnlyChannel <-chan ElementType, ... ){

//This function can only read from the given channel

}
```
- The above function can only read data from receiveOnlyChannel; it cannot write into the channel

Example:
```go
//ping fct can only write into pings channel

func ping(pings chan<- string, msg string){

pings <- msg

}
```
```go
//pong fct can only read from pings channel and write into pongs channel

func pong(pings <-chan string, pongs chan<- string){

msg := <- pings

pongs <- msg

}
```
Main:
```go
pings := make(chan string, 1)

pongs := make(chan string, 1)

ping(pings, "passed message")

pong(pings, pongs)

fmt.Println(<-pongs)
```
1. ping is writing passed message into the pings channel
2. pong is reading passed message from pings channel and writing passed message into the pongs channel
3. The main goroutine is reading and printing out passed message from the pongs channel

#### Range and Close

A go routine can close a channel if you're completely done with it
```go
close(channel)
```

Another go routine can use range to iterate through closed buffered channel
```go
for elem := range channel {

... Do stuff to each element in the channel

}
```

**Example**

The below function writes intermediate products into the go channel, and closes the channel once its done.
```go
func factorial(n int, channel chan int){

product := 1

for i:=1 ; i <= n; i++{

product *= i

channel <- product

}

close(channel)

}
```
In main:
```go
n := 5

factorialChannel := make(chan int, n)

go factorial(n, factorialChannel)

for elem := range factorialChannel {

fmt.Println(elem)

}
/* 
Console output
1
2
6
24
120
*/
```
The main function uses range in order to iterate through all the values in the closed factorialChannel.

#### Select

A go routine that uses select waits until it has read or written to a specified channel.

Syntax:
```go
select {

//Waits until channel's front is read into readVar

case readVar := <- channel:

...

//Waits until writeVar is queued into channel

case channel <- writeVar:

...

default:

...

}
```
- Notes

  - Blocking Send/Receive: Without default, select waits until something can be read from channel or written into it
  - Non-Blocking Send/Receive: With default, select does not wait for a send or receive case to be satisfied

**Example**
```go
channelSize := 3

sampleChannel := make(chan int, channelSize)

//Starts up 3 goroutines

for j := 0; j < channelSize ; j++ {

go countFromStartToEnd("Goroutine1", 0, j*2, j, sampleChannel)

}

//Waits for all goroutines to finish before moving on

numResponse := 0

for numResponse < channelSize {

select {

case response := <- sampleChannel:

fmt.Println(response)

numResponse++

//Implement default for non-blocking channel receives

/*

default:

fmt.Println("Nothing received yet.")

*/

}

}
```