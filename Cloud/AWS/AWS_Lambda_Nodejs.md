# Lambda runtime using Nodejs

## Lambda Handler

The Lambda function handler is the method in your function code that processes events. When your function is invoked, Lambda runs the handler method. When the handler exits or returns a response, it becomes available to handle another event.

The following example function logs the contents of the event object and returns the location of the logs.

```
exportfs.handler = async function(event, context) {
    console.log("Event: \n " + JSON.stringify(event,null,2))
    return context.logStreamName
}
```
Handlers have three arguments

1) Events
2) context
3) callback

### event

It is an object, which contains information from *invoker*. [Invoker: Invokes a Lambda function. You can invoke a function synchronously (and wait for the response), or asynchronously. To invoke a function asynchronously, set InvocationType to Event.] The invoker passes this information as a JSON formatted string. When invoke is run, it converts JSON to object.

### context

which contains information about the invocation, function, and execution environment. In the preceding example, the function gets the name of the log stream from the context object and returns it to the invoker.

### callback

It is a function that you can call in Non-async handlers to send response. The call back take two arguments

- Error 
- Response

When you call it, Lambda waits for the event loop to be empty and then returns the response or error to the invoker. 

The response object should be compatible with JSON.stringify() method.

For async handlers, you return a response, error, or promise to the runtime instead of using callback.

---

## Context in handler (Second argument of handler)

When Lambda runs your function, it passes a context object to the handler. This object provides methods and properties that provide information about the invocation, function, and execution environment.

The following example function logs context information and returns the location of the logs.

**index.js**

```
exports.handler = async function(event, context) {
  console.log('Remaining time: ', context.getRemainingTimeInMillis())
  console.log('Function name: ', context.functionName)
  return context.logStreamName
}
```

### explanation of above code

- **logStreamName** --> The log stream name of the function instance.

- **functionName** --> function name i.e Lambda function name.

- **getRemainingTimeInMillis() [this is method]** --> Returns the number of MilliSeconds left before execution time left.

---

## Async handlers

For async handlers, you can use return and throw to send a response or error, respectively. Functions must use the async keyword to use these methods to return a response or error.

If your code performs an asynchronous task, return a promise to make sure that it finishes running. When you resolve or reject the promise, Lambda sends the response or error to the invoker.

**Example index.js file – HTTP request with async handler and promises**

```
const https = require('https')
let url = "https://docs.aws.amazon.com/lambda/latest/dg/welcome.html"   

exports.handler = async function(event) {
  const promise = new Promise(function(resolve, reject) {
    https.get(url, (res) => {
        resolve(res.statusCode)
      }).on('error', (e) => {
        reject(Error(e))
      })
    })
  return promise
}
```

For libraries that return a promise, you can return that promise directly to the runtime.

**Example index.js file – AWS SDK with async handler and promises**

```
const AWS = require('aws-sdk')
const s3 = new AWS.S3()

exports.handler = async function(event) {
  return s3.listBuckets().promise()
}
```

---

## Non-async handlers

The following example function checks a URL and returns the status code to the invoker.

**Example index.js file – HTTP request with callback**

```
const https = require('https')
let url = "https://docs.aws.amazon.com/lambda/latest/dg/welcome.html"

exports.handler =  function(event, context, callback) {
  https.get(url, (res) => {
    callback(null, res.statusCode)
  }).on('error', (e) => {
    callback(Error(e))
  })
}
```

For non-async handlers, function execution continues until the event loop is empty or the function times out. The response isn't sent to the invoker until all event loop tasks are finished. If the function times out, an error is returned instead. You can configure the runtime to send the response immediately by setting context.callbackWaitsForEmptyEventLoop to false.

In the following example, the response from Amazon S3 is returned to the invoker as soon as it's available. The timeout running on the event loop is frozen, and it continues running the next time the function is invoked.

**Example index.js file – callbackWaitsForEmptyEventLoop**

```
const AWS = require('aws-sdk')
const s3 = new AWS.S3()

exports.handler = function(event, context, callback) {
  context.callbackWaitsForEmptyEventLoop = false
  s3.listBuckets(null, callback)
  setTimeout(function () {
    console.log('Timeout complete.')
  }, 5000)
}
```

---
## invoker

Invokes a Lambda function. You can invoke a function synchronously (and wait for the response), or asynchronously. To invoke a function asynchronously, set ```InvocationType``` to ```Event```.

For synchronous invocation, details about the function response, including errors, are included in the ```response body``` and ```headers```. For either invocation type, you can find more information in the ```execution log``` and ```trace```.

For asynchronous invocation, Lambda adds events to a queue before sending them to your function. If your function does not have enough capacity to keep up with the queue, events may be lost. Occasionally, your function may receive the same event multiple times, even if no error occurs. To retain events that were not processed, configure your function with a ```dead-letter queue```.

---

## JSON.stringify()

The common use of JSON is to exchange data to/from a webserver.

When sending data to a webserver, the data has to be a string.

It converts a javascript object into a string.

### Stringify a javascript object

```
const obj = {name:"john, age:30,city:"NewYork"}
```

Convert the above array into string using below code.

```
const myjson = JSON.stringify(obj);
```

myjson is string now.


### Stringify a JavaScript Array

It is also possible to stringify JavaScript arrays:

Imagine we have this array in JavaScript:

``` 
const arr = ["John", "Peter", "Sally", "Jane"];
```

Use the JavaScript function JSON.stringify() to convert it into a string.

```
const myJSON = JSON.stringify(arr);
```

