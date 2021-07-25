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

