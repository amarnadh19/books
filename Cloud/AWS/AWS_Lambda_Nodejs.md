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

It is a function that you can call in Non-sync handlers to send response. The call back take two arguments

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

---

## this keyword in javascript

Objects are the basic building blocks in JavaScript. There’s one special object available in JavaScript, the this object. You can see the value of this at every line of JavaScript execution. The value of this is decided based on how the code is being executed.

In most cases, the value of this is determined by how a function is called.

It can't be set by assignment during execution, and it may be different each time the function is called.


### “this” Refers to a Global Object

By default, the execution context for an execution is global — which means if a code is being executed as part of a simple function call, then this refers to a global object.

For example

```
const test = {
  prop: 92,
  func: function() {
    return this.prop;
  },
};

console.log(test.func());
// expected output: 92

```

In a NodeJS environment, a special object called global will be the value of this.

If strict mode is enabled for any function, then the value of this will be marked as undefined as in strict mode. The global object refers to undefined in place of the windows object.

### “this” Refers to a New Instance

When a function is invoked with the new keyword, then the function is known as a constructor function and returns a new instance. In such cases, the value of this refers to a newly created instance.

```
function Person(fn, ln) {
  this.first_name = fn;
  this.last_name = ln;

  this.displayName = function() {
    console.log(`Name: ${this.first_name} ${this.last_name}`);
  }
}

let person = new Person("John", "Reed");
person.displayName();  // Prints Name: John Reed
let person2 = new Person("Paul", "Adams");
person2.displayName();  // Prints Name: Paul Adams

```

In the case of person.displayName, this refers to a new instance person, and in case of person2.displayName(), this refers to person2 (which is a different instance than Person).


### “this” Refers to an Invoker Object (Parent Object)

In JavaScript, the property of an object can be a method or a simple value. When an object’s method is invoked, then this refers to the object which contains the method being invoked.

In this example, we’re going to use the method foo as defined in the first example.

```
function foo () {
  'use strict';
  console.log("Simple function call")
  console.log(this === window); 
}

let user = {
  count: 10,
  foo: foo,
  foo1: function() {
    console.log(this === window);
  }
}

user.foo()  // Prints false because now “this” refers to user object instead of global object.
let fun1 = user.foo1;
fun1() // Prints true as this method is invoked as a simple function.
user.foo1()  // Prints false on console as foo1 is invoked as a object’s method

```

```user.foo()``` prints false because now this refers to the user object instead of the global object.

  