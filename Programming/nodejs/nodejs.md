# 1. Introduction to Nodejs

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


# Output to the command line using Node.js


## Basic output using the console module

Node.js provides a console module which provides tons of very useful ways to interact with the command line.

It is basically the same as the console object you find in the browser.

The most basic and most used method is console.log(), which prints the string you pass to it to the console.

If you pass an object, it will render it as a string.

You can pass multiple variables to console.log, for example:

```
const x = 'x'
const y = 'y'
console.log(x, y)

```

console.log('My %s has %d years', 'cat', 2)

```
%s format a variable as a string
%d format a variable as a number
%i format a variable as its integer part only
%o format a variable as an object

```

## clear the console

```console.clear()``` clears the console

---

# Modules in Node.js

Node.js has vast libriaries (called in Javascript). These libraries are named as *Modules* in Node.js. 

To load modules we use inbuilt command *require*. It is function defined in Node.js

Node uses two core modules for managing module dependencies:

- The require module, which appears to be available on the global scope — no need to require('require').

- The module module, which also appears to be available on the global scope — no need to require('module').



## require()


*require()* is used to consume modules. It allows you to include modules in your app. You can add built-in core Node.js modules, community-based modules (node_modules), and local modules too.

```
EG: var <variablename> = require ('fs')

```

above command loads module name FS (Filesystem) which operates on Filesystem leve.


---

# Handling standard I/O

**STDIN** (standard in) refers to an input stream that a program can use to read input from a command shell or Terminal. 

**STDOUT** (standard out) refers to the stream that is used to write the output. 

**STDERR** (standard error) is a separate stream to STDOUT that is typically reserved for outputting errors and diagnostic data.


let's first create a single file named greeting.js. The program will ask for user input via STDIN, return a greeting via STDOUT, and log an error to STDERR when invalid input is provided. 

1) First, we need to tell the program to listen for user input. This can be done by adding the following lines to greeting.js:

```
process.stdin.on("data", (data) => {
// processing on each data event
});

```

2) We can run the file using the following command. Observe that the application does not exit because it is continuing to listen for process.stdin data events:

```
$ node greeting.js

```

3) Exit the program using CTRL + C.


4) We can now tell the program what it should do each time it detects a data event. Add the following lines below the // processing on each data event comment:

```
const name = data.toString().trim().toUpperCase();
process.stdout.write(`Hello ${name}!`);
```

5) You can now type some input in to your program, and it will return the greeting and your name in uppercase:

```
$ node greeting.js $ Beth   Hello BETH

```

6) We can now add a check for whether the input string is empty, and log to STDERR if it is. Change your file to the following:

```
process.stdin.on("data", (data) => {
	const name = data.toString().trim().toUpperCase();
	if (name !== "") {
		process.stdout.write(`Hello ${name}!`);
	} else {
		process.stderr.write("Input was empty.");
	}
});

```


## How it works

*process.stdin, process.stdout, and process.stderr* are all properties on the process object. 

A global process object provides the information and control of the Node.js process. 

For each of the I/O channels, they emit data events for every chunk of data received.

In this recipe, we were running the program in interactive mode where each data chunk was determined by the newline character when you hit Enter in your shell.

```process.stdin.on("data", (data) => {...});``` is what listens for these data events. Each data event returns a *Buffer object*. The Buffer object (typically named data) returns a binary representation of the input.

```const name = data.toString()``` is what turns the Buffer object into a string. The ```trim()``` function removes the newline character that denoted the end of each input.


We write to STDOUT and STDERR using the respective properties on the process object (process.stdout.write, process.stderr.write).

	Important note

Console APIs: Under the hood, ```console.log``` and ```console.err``` are using process.stdout and process.stderr.



---

# Managing files with fs module


