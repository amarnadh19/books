
# Javascript basics (essential for nodejs to understand program structure)

## Declaring Variables

A variable in JavaScript is an identifier whose value can be retrieved or set and is normally defined with the var keyword. Here is an example of a variable declaration:

```
var <variablename>;

Eg: var Name;

```

To actually assign a value to this variable and give it something useful to do, we must use the assignment operator, ```=```. Here is the same statement with a value assigned to the variable:

```
var Name = "amar"; // we assigned a string variable. Java script supports multiple types of variables. We will cover in future tutorial.

```

Multiple assignments

```
var firstName = "amar";
var lastName  = "tangeda";

console.log("hello" + firstName + lastName);

```

'+' used as concatination operator. It joins two strings.

console.log is a method to display output.


## Data Types

Some common JavaScript data types with their uses and descriptions are as follows:

- **number**: Any positive or negative value whole numbers, usually called integers and floating-point numbers, that can be used in mathematical operations. 

- **string**: Any set of valid characters that cannot be, or are not intended to be, used in computational operations. 

- **boolean**: Any value representing true and false. 

- **object**:  An unordered collection of values, called properties, and code, called methods, that are intended to work together.

- **function**: A specialized object data type that represents a block of code.


### Representation of Data


Data is represented in programs using expressions.

Expressions can be resolved to a value representing a specific data type.

Expressions can be broken down into smaller parts, as follows:

- Literal values

- Operators

- Variables

- Functions that return data

- Object properties

- Object methods that return data


#### Literal Values

Literal values are written into the programming code. Literal values are static. This means that they have the same value every time the line of code is executed, and they cannot be changed.


#### Using Operators in Expressions

Operators are used to performing arithmetic, combine text, make logical comparisons, and assign values to variables and properties.

The operators we look at can be grouped as follows:

- Arithmetic

- String

- Grouping

- Comparison

- Logical

- typeof

For math computations, we use arithmetic operators.

The string operator allows us to combine parts of an expression into a string value.

Below are some arithmetic operators in JS.

- ** --> exponentation  eg: 2 ** 3 = 8  (2 power 3)

- * --> Multiplication   eg: 2 * 3 = 6 

- + --> addition		 eg: 2 + 3 = 5

- - --> subtraction      eg: 3 - 2 = 1

- % --> Remainder        eg: 200 % 5 = 0


##### Grouping (concatenation (+))

It converts non-string data types into strings

```
"Blue" + "Moon"
"Blue" + " " + "Moon"
"$" + 100 * .10 + " discount"

```

The output for each would be as follows:

```
"BlueMoon"
"Blue Moon"
"$10 discount"
```


##### Operator Precedence

Expressions are not evaluated left to right. Instead, they are evaluated based on a preset operator order, which is called the operator precedence. For example, the multiplication operator has higher precedence than the addition operator does. You can override the operator's precedence using the grouping operator. It forces the evaluation of the expression contained within it before the rest of the expression is evaluated.

For example, the () operator controls the precedence of expression evaluation:

```
1 + 2 * 3
(1 + 2) * 3
10 + 10 * 5 + 5
(10 + 10) * (5 + 5)

```

The output for each of the preceding examples would be as follows:

```
7 
9
65
200

```

##### Comparing data

The resulting value of comparing data is either true or false. The following table describes certain comparison operators, along with examples:

![](https://github.com/amarnadh19/books/blob/main/images/js_1.jpeg?)


##### logical operators

Multiple parts of an expression can be compared using logical operators. These are sometimes called Boolean operators. Some Boolean operators, along with a description of them and examples, are as follows:


![](https://github.com/amarnadh19/books/blob/main/images/js_2.jpeg?)


##### typeof

A very helpful operator is typeof. It shows the data type as a string. 

For example, the typeof operator controls the precedence of expression evaluation:

```
typeof 100
TypeOf 100
typeof "100"
typeof true
typeof (1 > 2)
typeof (2 + " dozen eggs")
```

The output for each of the preceding examples would be as follows:

```
number
Uncaught SyntaxError: …
string
boolean
boolean
string
```

#### Using Variables and Constants in Expressions

The value of a variable can be changed after it is assigned. The value that's assigned to a constant cannot be changed

Variables and constants need to be declared before we can use them. For variables, there are two declaration keywords: **var and let**. 

For constants, the declaration keyword is **const**.

Variables and constants require a **name**.

The **assignment operator** is the single equals sign, =

The variable's **data type** is dynamic and is the same as the expression.

Variables do not need to be assigned a value when declared. A constant must be assigned a value when declared.

```
var firstName
var totalLikes
var errorMessage
var isSold
```

Variables that are not assigned a value still have a **data type**. That data type is named **undefined**. The typeof operator detects undefined data types.

Here are some examples of declaring a variable and assigning a value:

```
var firstName = "Albert"
var totalLikes = 50
var errorMessage = "Something terrible happened"
var isSold = false
```


#### Functions That Return Values

Functions may be written to return a value. In that case, we can use them in expressions. When we use a function, it is also called invoking the function.

To use a function in an expression, you need to include the function name, followed by parentheses. If the function requires input, it is placed inside the parentheses as valid expressions. These are called arguments. If more than one argument is needed, they are separated with commas.

These examples assume that the function will return a value.

Have a look at this example on expressing functions that do not require an argument:

```
getTotal() 
isLoggedIn()
```

This example shows us expressing a function that has one argument expressed as a number literal:

```
getCelsiusFromFahrenheit(32)

```

This example shows us expressing a function that has multiple arguments using literal values:

```
getSearchResults("Pet Names", 25)

```

Finally, this example shows us expressing a function that has multiple arguments using variables:

```
var amount = 100000
var decimals = 2
var decimalSeparator = "."
var thousandsSeparator = ","
formatCurrency(amount, decimals, decimalSeparator, thousandsSeparator)

```


### The Object Data Type

JavaScript is designed around object data, thus making it important to understand. There are JavaScript objects that have been ready-made for us to use and you, as a programmer, will create objects. In either case, JavaScript objects are composed of **properties and methods**:

**Property:** A value that has an assigned named. Together, they are often called a name/value pair. Values can be any type, that is, data, a number, a string, a Boolean, or an object. Property values can be changed dynamically.

**Method:** A function that performs an action.


#### Ready-Made Objects

JavaScript has ready-made objects that we can use to help us begin to learn how to program. There are many useful objects built into JavaScript. Web browsers provide a collection of objects called the Document Object Model (DOM).

Some examples of ready-made objects are as follows:

- window is an object in DOM. It has access to the web browser's open window. Often considered a top-level DOM object containing other web browser-created objects as its properties, it has methods for setting timer events and printing.

- console is an object in DOM. It provides the ability to output to the web browser console window. It is also a property of the window object.

- document is an object in DOM. It has access to a web page's HTML elements, styles, and content. It is also a property of the window object.

- location is an object in DOM. It has information about the current URL. It is a property of the window object.

- Math is a built-in object. It consists of math constants such as Pi, and functions such as rounding.

- Date is a built-in object. It provides calendar date and time operations.


#### Self-Made Objects

You often have to create objects when developing real-world applications.

- elapsedTime is a property with a data type number. It displays the seconds that have elapsed since timing started.

- resultsHistory is a property data type object. It displays a list of previous timings.

- isTiming is a property data type Boolean. It displays the state of its timing.

- isPaused is a property data type Boolean. It displays the state if paused.

- start is a method data type function. It starts timing and sets elapsedTime to 0.

- pause is a method data type function. It pauses the timing.

- resume is a method data type function. It resumes the timing.

- stop is a method data type function. It stops timing and adds the result to resultsHistory.


#### Object Dot Notation

To reference object properties and methods, you use dot notation. This is the object name, followed by a period, and then the name of the property or method. Let's use the stopWatch object as an example:

```
stopWatch.elapsedTime
stopWatch.start()
stopWatch.start()
stopWatch.stop()

```

Methods require parentheses after the name. If the method requires data input, the data is placed inside the parentheses.


#### The Array Object


---