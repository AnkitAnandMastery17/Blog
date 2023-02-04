# Learning JavaScript

## Why JavaScript?

* Language of the web
    
* It is the only computer language that allows us to directly interact with our web pages dynamically on the client side
    
* Easy to use
    
* It is used widely
    
* JavaScript skill is in demand
    

### **Comments in JavaScript**

There are two varieties of comments in JavaScript:

1. Single-line comments
    
2. Multi-line comments
    
    ***A single-line comment*** is created when you add two forward-slash characters one after the other, without spaces.
    
    Eg. // this is a comment!
    

***A multi-line comment***, as its name says, spans several lines of code and is created with a forward slash and a star. For example:

```jsx
/*
this
is
a
multi-line
comment
*/
```

**Why writing comments is empowering?**

* You can now freely express your ideas about any code that you write.
    
* You can add comments to any code that already exists.
    
* Those comments can be intended for your future self, or for colleagues on your development team.
    

There can be many reasons for that:

* Trying to understand how a given piece of code works.
    
* Testing different solutions to a coding problem - while not having to delete existing code.
    
* Debugging - trying to pinpoint why your code is broken or behaving unpredictably.
    

### **Comments in JavaScript:-**

There are two varieties of comments in JavaScript:

1. Single-line comments
    
2. Multi-line comments
    

***A single-line comment*** is created when you add two forward-slash characters one after the other, without spaces.

1. // this is a comment!
    

A multi-line comment, as its name says, spans several lines of code and is created with a forward slash and a star. For example:

```jsx
/*
this
is
a
multi-line
comment
*/
```

### **Why writing comments is empowering?**

1. You can now freely express your ideas about any code that you write.
    
2. You can add comments to any code that already exists.
    
3. Those comments can be intended for your future self, or for colleagues on your development team.
    

There can be many reasons for that:

1. Trying to understand how a given piece of code works.
    
2. Testing different solutions to a coding problem - while not having to delete existing code.
    
3. Debugging - trying to pinpoint why your code is broken or behaving unpredictably.
    

### **The semi-colon in JavaScript**

In JavaScript, the semi-colon - the**;** character - has a similar purpose: it is used to clearly delimit parts of the code from some other parts of the code.

### Console.log trick

Here's another, more complex command, to show you that the **console.log** command comes with a number of tricks.

For example, did you know that you can style the output in the console?

In this code snippet, there are a few additions: the font size is different and the color is blue:

```javascript
           console.log("%cHello, World", "color: blue; font-size: 40px");
```

### Variables-

It is a container that stores values.

### Data types-

There are 7 types of data types in JavaScript. The names are mentioned below-

* String
    
* Number
    
* Boolean
    
* Null - Absence of a value
    
* Undefined - unassigned value
    
* BigInt - Very large range of numbers
    
* Symbol
    

### **Operator precedence and associativity**

***Operator precedence*** is a set of rules that determines which operator should be evaluated first.

Here is the operator precedence in JavaScript, from highest to lowest:

1. `()` (parentheses)
    
2. `**` (exponentiation)
    
3. `!`, `~`, `++`, `--`, `+`, `-` (unary operators)
    
4. `*`, `/`, `%` (multiplicative operators)
    
5. `+`, `-` (additive operators)
    
6. `<<`, `>>`, `>>>` (bitwise shift operators)
    
7. `<`, `<=`, `>`, `>=`, `instanceof`, `in` (relational operators)
    
8. `==`, `!=`, `===`, `!==` (equality operators)
    
9. `&` (bitwise AND operator)
    
10. `^` (bitwise XOR operator)
    
11. `|` (bitwise OR operator)
    
12. `&&` (logical AND operator)
    
13. `||` (logical OR operator)
    
14. `? :` (conditional operator)
    
15. `=`, `+=`, `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `>>>=`, `&=`, `^=`, `|=` (assignment operators)
    
16. `yield`, `await` (yield and await operators, in ECMAScript 2017+)
    

***Associativity*** determines the order in which operations with the same precedence are performed.

Here is the associativity in JavaScript, from left to right:

1. Assignment operators (`=`, `+=`, `-=`, `*=`, `/=`, `%=`, `<<=`, `>>=`, `>>>=`, `&=`, `^=`, `|=`)
    
2. Logical OR operator (`||`)
    
3. Conditional operator (`? :`)
    

All other binary operators, such as arithmetic operators (`+`, `-`, `*`, `/`, etc.), comparison operators (`<`, `>`, `<=`, `>=`, `==`, `!=`, `===`, `!==`), and bitwise operators (`&`, `^`, `|`, `<<`, `>>`, `>>>`), are right-to-left associative.