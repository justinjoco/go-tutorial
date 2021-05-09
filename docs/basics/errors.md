### Error Handling ([https://repl.it/@jjoco/go-error-handling](https://repl.it/@jjoco/go-error-handling))

Some functions return an error type

sampleVar, err := canReturnErrorFct(args)

if err != nil {

//Do something if there&#39;s an error

}

If the function is successful, err would be nil.

##### Example:

sampleStr := &quot;ffgds&quot;

strToInt, err := strconv.Atoi(sampleStr)

if err != nil {

log.Fatal(err)

}

fmt.Println(strToInt)

// Output = &quot;2020/10/22 19:39:38 strconv.Atoi: parsing &quot;ffgds&quot;: invalid syntax&quot;

// &quot;exit status 1&quot;

#### Ignoring error

If you&#39;re feeling ambitious, you can certainly skip error handling of a function like below using \_:

sampleVar, \_ := canReturnErrorFct(args)

However, only do this if you&#39;re really confident that the function will not return an error ever