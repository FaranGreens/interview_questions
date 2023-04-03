### What is JS and Purpose of it?

JavaScript is a scripting or programming language that allows you to implement complex features on web pages — every time a web page does more than just sit there and display static information for you to look at — displaying timely content updates, interactive maps, animated 2D/3D graphics, scrolling video jukeboxes, etc. — you can bet that JavaScript is probably involved. It is the third layer of the layer cake of standard web technologies

### What is execution context in JS?
In JavaScript, the execution context refers to the environment in which a piece of code is executed.
everything happens inside execution context in javascript.

Execution context has two parts:
1. Memory component aka variable environment: all the variables and functions are stored as key value pairs
2. Code component aka thread of execution
javascript is a synchronous single threaded language. one command at a time and in a speciific order.

### what happens when you run a javascript program? Or how js program is executed?
phase - 1: global execution context is created: memory creation phase - variable memory is allocated and undefined value is assigned to it.
function is saved with the whole code. when function is called a new local execution context is created and two phases of execution context happens. When it ends / returns the control to the where it was called from, the execution context is deleted.

phase 2: code is executed line by line.

everything is managed in call stack. global execution context is in the bottom of the stack. whenever a function is invoked or local execution context is created it is put inside the stack and is cleared when its execution is completed.

when whole program is done or execution completes, the global execution context is deleted as well and the call stack is empty.
call stack maintains the execution of execution contexts.

call stack is also known by many names -> execution context stack, prog stack, control stack, runtime stack, machine stack etc.

### The scope chain and lexical environment:
In JavaScript, the scope chain is a list of Variable Objects (VOs) that are used to 
resolve variables and functions during the execution of code.

When a variable or function is referenced in code, the JavaScript engine 
searches through the Variable Object of the current execution context, 
and if it doesn't find it there, it moves up the scope chain until 
it finds the variable or function or reaches the global scope (window object in web browsers).

The scope chain is created at the time when the execution context is created. 
Each execution context has a reference to its outer (enclosing) environment, 
which is used to build the scope chain.

The outer environment is typically the parent function or global environment. 
When a function is defined inside another function, it creates a new scope 
that is nested inside the scope of the outer function, forming a chain of nested scopes.

The scope chain is important in JavaScript because it affects how variables 
and functions are accessed and modified. Variables defined in an 
outer scope are accessible from inner scopes, but variables defined 
in an inner scope are not accessible from outer scopes.


lexical environment is the structure that holds information about the variables and
 functions that are available in the current scope, as well as the reference to the 
 outer (enclosing) lexical environment.

The lexical environment is created at the time when a function is defined, and it is
 determined by where the function is defined in the code (i.e., its "lexical" 
 position). When a function is called, a new execution context is created, and the 
 current lexical environment becomes the Variable Object of the new execution context.
 
The lexical environment consists of two parts:

1. Environment Record - It is a data structure that holds the identifiers (variables and functions) defined in the current scope and their corresponding values.

2. Reference to the outer (enclosing) lexical environment - It is a reference to the lexical environment of the parent scope, which is used to resolve variable and function names that are not defined in the current scope

### Temporal Dead Zone:
teporal dead zone is the time between the let or const is defined and being initialised.
Let and const are also hoisted in javascript but they hoisted differently than var.
they are being in temporal zone before initialization.
They cannot be accessed in global execution context/scope or using window or this.
best practice is to move our declaration and initialisation on the top of the page to shrink the temporal dead zone to zero.

### Block scope and shadowing:
block is defined by {} 'curly braces ' also known as compound statements. we compound statements in one place when we need to write multiple statements.

Block scope:  what all variables and functions we can access inside the block.
They will be hoisted in block scope and not in global scope.
if var, let and const all are defined inside {} or block. var is accessed inside global scope but let and const are not.
which is why let and const are called block scoped.
block follows lexical scope chaining if we want to access any values.

Shadowing:
we can redeclare a variable inside a scope and it will overwrite temporarily its value for computation inside the scope.
let and const can be shadowed as well.

### What are Data types in JS

JavaScript has 8 Datatypes
1. String
2. Number
3. Bigint
4. Boolean
5. Undefined
6. Null
7. Symbol
8. Object



The Object Datatype
The object data type can contain:

1. An object
2. An array
3. A date

![JS_datatypes](JS_datatypes.png)

### Closure

A closure is the combination of a function bundled together (enclosed) with references to its surrounding state (the lexical environment). In other words, a closure gives you access to an outer function's scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

### Explain Closures, Why do we need it
A closure is a feature in JavaScript that allows a function to access variables outside of its own scope.
In other words, a closure "closes over" or captures the variables that are in the surrounding environment,
so that the function can use them even if they would otherwise be out of scope.

use cases:
Factory functions: Closures can be used to create factory functions that return new functions with specific behavior,
while also capturing and preserving private state.

Event handling: Closures can be used to create event handlers that remember information about
the state of the application at the time the event was triggered.

Memoization: Closures can be used to cache the results of expensive function calls,
improving the performance of the application by avoiding unnecessary computations.

Currying: Closures can be used to implement currying, which is a technique for transforming a
function with multiple arguments into a series of functions that each take a single argument.

Asynchronous programming: Closures can be used to manage the flow of asynchronous code,
by capturing and preserving state across multiple asynchronous operations.

data hiding/encapsulation.

```
setTimeout and closure



```
### Functions and types
```JS
a(); // properly hoisted, no error
b(); // will throw error as code doesnot know b is a function yet and its undefined
//treated like a normal variable.
//Function statement: this way of making function is function statement aka Function declaration
function a(){
    //some code
}

//Function expression:
// the diff b/w fn expression and fn statement is in hoisting.
var b = function (){
    //some code
}
b(); //called here then no error as b is not undefined.

//Anonymous Function: func without a name. they are used when functions are used as a value.
function (){

}

//named functions

//diff b/w parameters and arguments
//parameters are labels or identifiers when we define a function. they get the value passed from arguments
//when function is called. they are treated as local variables. they are in local scope only.
function fn(param1, param2){
    //some code
}
fn(arg1, arg2);

//first class function: the ability of functions to be used as value and passed as arguments to other
// functions and can be returned from other functions.

//first class citizens

//arrow functions:came as a part of ES6:

```

## Event Loop

Microtask queue: promises, mutation observers go in microstask queue. microtask queue has higher priority.

Callback queue: all other callback fns go in task queue or call back queue. it will execute once microstask queue has become empty.

Starvation:

</br>

## JS Engine

Javascript runtime Environment: JavaScript runtime environment refers to the environment or context in which JavaScript code is executed. It includes all the necessary components that are required to run JavaScript code, such as the browser or Node.js.

3 steps in JS engine
parsing: code broken into tokens. syntax parser breaks code in AST (abstract syntax tree).AST is passeddown to compilation phase

compilation: compilation and execution work hand in hand. jS has JIT(just in time) compilation. Js can use both interpreter and compiler to make it work.
It converts ASt to byte code and sends for execution. Compilation does alot of optimization like - inlining, copy elision, inline caching

execution: it uses memory heap and call stack to execute the byte code. grbage collector tries to clear memory using mark and sweep algorithm.

V8 has interpreter named - ignition, along with that turbo-fan as optimizing compiler. garbage collector are orinoco and oilpan.

## Higher order function

a function which takes a function as an argument or returns a function as value is known as higher order function.

## Callbacks
a callback is a function that is passed as an argument to another function and is executed when that function has completed its operation.

### Callback hell

alot of nested callbacks. callback inside callback. aka pyramid of doom.

#### Inversion of control

you lose the control of code while using callback.

## Promises

used to handle async operations. can be resolved once. 3 state - pending, fulfilled, rejected.
promise object data is immutable.
a promise is an object which represents the eventual completion or failure of an async operation.

### why do we use promise?

promise create trust in the transaction.<br/>
Promises simplify asynchronous code by eliminating the need for nested callbacks, or "callback hell".<br/>
Promises provide a more structured way to handle errors, by allowing developers to attach a single error handler to a chain of asynchronous operations.<br/>
Promises support composition and chaining, which makes it easier to build complex asynchronous workflows.<br/>
Promises are a standardized API that is supported by modern browsers and Node.js, which makes it easier to write portable code.

### Promise chaining

promise chaing helps us to get out of callback hell.
fn.then(()=> fn2).then(()=>fn3)

### Creating Promises

```JS
function myFunc(arg){
    const promise = new Promise(function(resolve, reject){

        if(verificationFailed){
            const err = new Error("failed")
            reject(err);
        }

        const data = "data";
        if(data){
            resolve(data);
        }
    })
}

```


<br/>


### What is var , let and Const
var was the original keyword used to declare variables in JavaScript, but it has some quirks that can lead to unintended behavior. In particular, variables declared with var are function-scoped, meaning that their scope is limited to the function in which they are declared or to the global scope if they are declared outside of any function. var variables can also be redeclared and reassigned within their scope, which can lead to unexpected behavior.

let and const were introduced in ECMAScript 2015 as alternatives to var. Variables declared with let are block-scoped, meaning that their scope is limited to the block in which they are declared (i.e., a set of curly braces {}). let variables can be reassigned within their scope, but they cannot be redeclared.

const is similar to let in that it is also block-scoped, but it has an additional restriction: once a variable is declared with const, its value cannot be reassigned. const variables are commonly used to declare constants, such as mathematical or physical constants, that should not be modified during the execution of the program.

<br/>

### Explain Diff btw number data type and BigInt
In JavaScript, the Number data type is used to represent numbers, including integers and floating-point numbers, within a certain range. The range of numbers that can be represented by the Number data type is limited by the IEEE 754 standard, which defines a 64-bit format for representing numbers in binary.

BigInt, on the other hand, is a relatively new data type that was introduced in ECMAScript 2020. BigInt is used to represent integers of arbitrary length, beyond the maximum limit of the Number data type. BigInts are represented using a different format than regular numbers, which allows them to have an arbitrary length and precision.

The main differences between the Number data type and BigInt are:

Range: The range of the Number data type is limited to approximately ± 9 quadrillion (i.e., 2^53), while BigInt can represent integers of arbitrary length and magnitude.

Precision: The Number data type has a limited precision due to the nature of its binary representation, which can lead to rounding errors in certain calculations. BigInt, on the other hand, has arbitrary precision, which means that it can represent exact values without rounding errors.

Operators: Some operators and functions that work with regular numbers (e.g., +, -, *, /) may not work with BigInts, or may have different behavior due to the different format of the BigInt data type.

Syntax: BigInt literals are written with a trailing n, for example, const big = 123456789012345678901234567890n; whereas regular numbers do not have any specific syntax.

In summary, while the Number data type is suitable for representing most numerical values in JavaScript, BigInt is useful for cases where the range or precision of regular numbers is not sufficient, such as cryptography or mathematical algorithms that require large integer calculations.

<br/>

### Explain about Control statement and diff btween if else if and switch
control statements are used to control the flow of execution of a program based on certain conditions. There are several types of control statements in JavaScript, including if/else, switch, for, while, do/while, and break/continue.

The if/else statement is used to execute a block of code if a certain condition is true, and a different block of code if the condition is false. The else if statement allows you to test for additional conditions after the initial if statement, and execute a different block of code depending on which condition is true.

The switch statement is another way of testing for multiple conditions and executing different blocks of code depending on which condition is true. The main difference between if/else if and switch is that switch can be more concise and easier to read when testing for a large number of conditions, particularly if the conditions involve checking the value of a single variable.

<br/>

### What is Object and Array
an object is a collection of key-value pairs, where each key is a string (or a symbol in ES6+) and each value can be of any type, including other objects. Objects can be created using object literal syntax or using the new Object() constructor.

An array is a special type of object in JavaScript that stores a collection of values, where each value is identified by an index. Arrays can be created using array literal syntax or using the new Array() constructor.


### Explore All Array Methods and String Methods

### Diff between forEach() Map() and filter()

### Diff between slice and splice

### Diff btw == and ===

### What is for..in and for.. of

### What is DOM and DOM Manipulation

### What is call apply bind ?

```js
let name = {
  firstname: "adam",
  lastname: "driver",
  printFullname: function () {
    console.log(this.firstname + " " + this.lastname);
  },
};

let name2 = {
  firstname: "sachin",
  lastname: "kumar",
};
// using call method we can use function borrowing. we can borrow function from different objects.
// inside parenthesis we have give the reference to the this keyword. 
//in this case this is pointing towards name2 object.
name.printFullname.call(name2); //o/p : sachin kumar

//we can also refactor like this

let name = {
  firstname: "adam",
  lastname: "driver",
  //took out the function as a separate piece of code
};
function printFullname(town, country) { //added another parameter town
  console.log(this.firstname + " " + this.lastname + " from "+ town + ", " + country);
}

printFullname.call(name, "Delhi", "India") //first argument will be reference of this keyowrd
//second will be the argument for function.


printFullname.apply(name, ["Delhi", "India"]) 
//in apply method we pass second argument in as a list/array. rest working is same.

//bind method gives  copy of the function binded to the object.
//it doesnt invoke the method right away like call and apply rather it 

let printFunc = printFullname.bind(name, "London", "UK");
printFunc(); //o/p: adam driver from London, UK.

```

### polyfills for bind
polyfill is a browser fallback for a function that might not be supported in older browsers.

```js
let obj = {
    name:"adam",
    city:"delhi"
}
function print(country){
    console.log(this.name + " lives in " + this.city + ", "+country + " age " + this.);
}

let printfn = print.bind(obj, "India");
printfn("28")
Function.prototype.mybind = function(...args){
    let func = this;
    let params = args.slice(1);
    return function(...args2){
        func.apply(args[0], params);
    }
}

//now our mybind is ready

let printfn2 = print.mybind(obj, "India");
printfn2("25");

```
### Function Currying
Currying is a technique in functional programming where a function with multiple arguments is transformed into a series of functions that each take a single argument. The result of each function is a new function that expects the next argument in the series.

```js
//consider a function that calculates the sum of three numbers:
function sum(a, b, c) {
  return a + b + c;
}
//Using currying, we can transform this function into a series of functions that each take a single argument

function sumCurried(a) {
  return function(b) {
    return function(c) {
      return a + b + c;
    }
  }
}

// Usage
const sumResult = sumCurried(1)(2)(3);
console.log(sumResult); // 6

```
Using currying can make code more modular and composable by allowing functions to be partially applied, which means that some arguments can be fixed in advance, creating a new function that expects only the remaining arguments. This can make it easier to create reusable code that can be customized for different use cases.

<br />

### Polyfills for map, filter and reduce.
```js
Array.prototype.myMap = function(callback){
    let res = [];
    for(let i=0; i<this.length; i++){
        res.push(callback(this[i], i, this));
    }

    return res;
}

Array.prototype.myFilter = function(callback){
    let res = [];

    for(let i=0; i<this.length; i++){
        if(callback(this[i], i, this)) res.push(this[i]);
    }
    return res;
}

Array.prototype.myReduce = function(callback, initVal = null){
    let acc = initVal;
    for(let i=0; i<this.length; i++){
        acc = callback(acc, this[i], i, this)
    }

    return acc;
}
//approach 2
Array.prototype.myReduce = function(callback, initVal = null, thisArg){
    let acc = initVal;
    for(let i=0; i<this.length; i++){
        acc = callback.call(thisArg, acc, this[i], i, this)
    }

    return acc;
}

```

### What is Promise and Explain Promise

### What is Promise Chain

### In how many ways we can handle Promise

### Why do we need Promise

### What are the states of Promise Object

### Explain Fetch

### Why we need to handle then() two times in fetch

### What is async await

### What is OOPs and Explain its Features

### What is diff btw spread Operator and rest Parameter

### Explain about this keyword in JS
the this keyword in JavaScript refers to the current execution context, which is determined at runtime based on how the function is called

### Explain Prototype, prototype chain and prototypal inheritance
In JavaScript, each object has an internal property called [[Prototype]] (also called __proto__ in some contexts) that points to another object, called its prototype. This prototype object in turn has its own prototype, and so on, creating a chain of objects known as the prototype chain.

When you access a property of an object, JavaScript first checks if the object itself has that property. If it does not, JavaScript follows the prototype chain until it finds an object that does have the property, or until it reaches the end of the prototype chain (which is the Object.prototype object).

The mechanism of using the prototype chain to look up properties is known as prototypal inheritance, and it allows objects to inherit properties and methods from their prototypes, creating a flexible and powerful system for object-oriented programming in JavaScript.

### What is event

### Explain Event Propagation

### Explain diff btween Event Bubbling and Event Capturing

### How can we restrict Event Bubbling and Event Capturng behaviour

### What is Generator function in JS
Generator functions are a special type of function in JavaScript that allow you to pause and resume the execution of a function. When a generator function is called, it returns a generator object, which can be used to control the execution of the function.

Generator functions are defined using the function* syntax, which is similar to a normal function, but with an asterisk after the function keyword. Inside a generator function, you can use the yield keyword to pause the execution of the function and return a value to the caller. You can then resume the execution of the function later using the next() method on the generator object.
Generator functions can be very useful when you need to generate a sequence of values that may take a long time to compute, or when you need to generate values on demand based on some input. They can also be used to implement complex control flow patterns, such as asynchronous programming using promises and async/await.

<br/>

### What is diff between normal function and arrow function

### How to compare Object and How to find the Object is empty or not

### What is Set

### SetTimeout and setInterval

### What is Browser Object Model (BOM)

### Explain Storages of Browser

### Regular Expressions

### Explain Module Concept in JS

### Debouncing

### Throttling

### Async vs defer
