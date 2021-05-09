### Go Channels ([https://repl.it/@jjoco/go-channels](https://repl.it/@jjoco/go-channels))

Go channels is the method of communication that allows go routines to talk to each other. These are FIFO. The dev has to define the type that goes into the channel. The type can be anything: structs, maps, slices, primitives, etc.

If two go routines were processes, the go channel is the bridge between them:

![](RackMultipart20210429-4-9wxods_html_677f3f0ba8ab694d.png) ![](RackMultipart20210429-4-9wxods_html_4799d831b78abbe0.png)

#### Non-Buffered Channels

By default channels are _unbuffered_, meaning that they will only accept sends (chan \&lt;-) if there is a corresponding receive (\&lt;- chan) ready to receive the sent value

Syntax:

channel := make(chan ElementType)

#### Buffered Channels

_Buffered channels_ accept a limited number of values without a corresponding receiver for those values. These are much more flexible than unbuffered channels.

channel := make(chan ElementType, channelSize)

#### Reading and Writing to Channels

The \&lt;- denotes which way a value is getting written into

##### Writing

channel \&lt;- writeValue

- writeValue is getting written into channel

##### Reading

readVar \&lt;- channel

- The front of channel is getting read into declared variable readVar

##### Non-buffered example:

- A go routine is writing into nonBufferedChannel and has a receive in the main goroutine

nonBuffedChannel := make(chan string)

go func(){

nonBuffedChannel \&lt;- &quot;ping&quot;

}()

fmt.Println(\&lt;-nonBuffedChannel)

fmt.Println(&quot;Finished&quot;)

This will not work:

messages := make(chan string)

messages \&lt;- &quot;no&quot;

fmt.Println(\&lt;-messages)

fmt.Println(&quot;Done&quot;)

This will not run correctly because there is no immediate receiver (eg a concurrent receiver) for the send into messages

##### Buffered Examples

messages := make(chan string, 2)

messages \&lt;- &quot;hello there&quot;

messages \&lt;- &quot;general kenobi!!&quot;

fmt.Println(\&lt;-messages)

fmt.Println(\&lt;-messages)

- Strings are getting written into the messages channel and read out in a FIFO way

#### Uni-directional Channels

A function can be configured to be able to only read from a given channel or be forced to only write into a channel. This is used for type safety, and it ensures no two go routines can write to the same channel.

**Send-Only**

func functionName(sendOnlyChannel chan\&lt;- ElementType, ... ){

//This function can only write into the given channel

}

- The above function can only write data into sendOnlyChannel; it cannot read from the channel

**Receive-Only**

func functionName(receiveOnlyChannel \&lt;-chan ElementType, ... ){

//This function can only read from the given channel

}

- The above function can only read data from receiveOnlyChannel; it cannot write into the channel

Example:

//ping fct can only write into pings channel

func ping(pings chan\&lt;- string, msg string){

pings \&lt;- msg

}

//pong fct can only read from pings channel and write into pongs channel

func pong(pings \&lt;-chan string, pongs chan\&lt;- string){

msg := \&lt;- pings

pongs \&lt;- msg

}

Main:

pings := make(chan string, 1)

pongs := make(chan string, 1)

ping(pings, &quot;passed message&quot;)

pong(pings, pongs)

fmt.Println(\&lt;-pongs)

1. ping is writing passed message into the pings channel
2. pong is reading passed message from pings channel and writing passed message into the pongs channel
3. The main goroutine is reading and printing out passed message from the pongs channel

#### Range and Close

A go routine can close a channel if you&#39;re completely done with it

close(channel)

Another go routine can use range to iterate through closed buffered channel

for elem := range channel {

... Do stuff to each element in the channel

}

##### Example:

The below function writes intermediate products into the go channel, and closes the channel once its done.

func factorial(n int, channel chan int){

product := 1

for i:=1 ; i \&lt;= n; i++{

product \*= i

channel \&lt;- product

}

close(channel)

}

In main:

n := 5

factorialChannel := make(chan int, n)

go factorial(n, factorialChannel)

for elem := range factorialChannel {

fmt.Println(elem)

}

1

2

6

24

120

The main function uses range in order to iterate through all the values in the closed factorialChannel.

#### Select

A go routine that uses select waits until it has read or written to a specified channel.

##### Syntax:

select {

//Waits until channel&#39;s front is read into readVar

case readVar := \&lt;- channel:

...

//Waits until writeVar is queued into channel

case channel \&lt;- writeVar:

...

default:

...

}

- Notes
  - Blocking Send/Receive: Without default, select waits until something can be read from channel or written into it
  - Non-Blocking Send/Receive: With default, select does not wait for a send or receive case to be satisfied

##### Example

channelSize := 3

sampleChannel := make(chan int, channelSize)

//Starts up 3 goroutines

for j := 0; j \&lt; channelSize ; j++ {

go countFromStartToEnd(&quot;Goroutine1&quot;, 0, j\*2, j, sampleChannel)

}

//Waits for all goroutines to finish before moving on

numResponse := 0

for numResponse \&lt; channelSize {

select {

case response := \&lt;- sampleChannel:

fmt.Println(response)

numResponse++

//Implement default for non-blocking channel receives

/\*

default:

fmt.Println(&quot;Nothing received yet.&quot;)

\*/

}

}
