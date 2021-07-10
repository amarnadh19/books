
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


#### Grouping (concatenation (+))

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


#### Operator Precedence

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

#### Comparing data

The resulting value of comparing data is either true or false. The following table describes certain comparison operators, along with examples:

![](https://github.com/amarnadh19/books/blob/main/images/js_1.jpeg?)


#### logical operators

Multiple parts of an expression can be compared using logical operators. These are sometimes called Boolean operators. Some Boolean operators, along with a description of them and examples, are as follows:


![](https://github.com/amarnadh19/books/blob/main/images/js_2.jpeg?)


#### typeof

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



---