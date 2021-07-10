# 1. Introduction

Prior to Node.js, JavaScripts runs only under a web browser (such as Chrome, Firefox, and MSIE) bundled with a built-in JavaScript engine. Node.js is a JavaScript Runtime Engine that allows us to run JavaScript in standalone manner, without using a browser.

Node.js is commonly-used for programming web server, i.e., server-side JavaScript. This is popular because you can use the same JavaScript language to program the client and the server.

The mother site of Node.js is https://nodejs.org/.

The important features of Nodes.js are:

- Node.js runs the high-performance V8 JavaScript engine, the core of Google Chrome, outside of the browser.

- Node.js uses asynchronous programming. It provides a set of asynchronous non-blocking I/O functions (with new keywords *async and await*). Instead of blocking the thread and wasting CPU cycles waiting, Node.js will suspend the first request, continue with the next request, and resume the operations when the response of the first request comes back. This allows a Node.js app to run in a single process, without creating a new thread for every request. A Node.js server can handle thousands of concurrent connections without the burden of managing thread concurrency.

- You can program the client and server using the same JavaScript language.

- A huge number of libraries is available, which are managed by npm (Node package manager).

- Node.js is free, open-source, and runs under many platform (Linux, Windows, macOS).


# 2. Getting started with Node.js

**Running Node.js in REPL (Read-Evaluate-Print Loop) Command-Line Mode**

Start a CMD/Terminal/Bash-Shell. Launch Node.js:

```
$node
Welcome to Node.js v12.16.1.
Type ".help" for more information.
> .help
.break    Sometimes you get stuck, this gets you out
.clear    Alias for .break
.editor   Enter editor mode
.exit     Exit the repl
.help     Print this help message
.load     Load JS from a file into the REPL session
.save     Save all evaluated commands in this REPL session to a file
Press ^C to abort current expression, ^D to exit the repl

> console.log("hello, world")
hello, world
undefined   // return value of console.log() function
> .exit     // or Ctrl-C twice, or Ctrl-D
```

Node.js runs in the REPL (Read-Evaluate-Print Loop) mode - an interactive language shell. It takes a single user input, evaluates, and returns the result.

**Executing JavaScript Source Files**

Prepare a JavaScript called "hello.js" as follows:
```
// hello.js
console.log('hello, world');
```
You can run the Script under Node.js as follows:
```
$node hello.js
hello, world
```

