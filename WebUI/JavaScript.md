# Java Script

#### Navigation
- [Basics](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#basics)
 - [Fundamental Examples](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#fundamental-examples)
 - [JS Types](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#js-types)
 - [Undefined and Null Types](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#undefined-and-null-types)
 - [NaN Value](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#nan-value)
 - [JS Arrays](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#js-arrays)
 - [Specific Operators](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#specific-operators)
 - [Conversion Methods](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#conversion-methods)
 - [Date Object](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#date-object)
 - [Typical Loops](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#typical-loops)
 - [JS Events](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#js-events)
- [Functions, Closures, Objects, Prototypes](https://github.com/kakarotto67/KnowledgeBank/blob/master/WebUI/JavaScript.md#functions-closures-objects-prototypes)

#### Basics
- JavaScript is case-sensitive
- JavaScript is based on ECMAScript standard. Latest version of this standard (ECMAScript6, ES6, ES 2015) includes new capabilities such as classes, modules, iterators, arrow functions, collections, etc. Other realizations of ECMAScript: ActionScript, JScript, etc.
- JavaScript isn't strongly typed language

###### Fundamental Examples

```js
var x = 16 + 4 + "v"; // 20v
var y = "v" + 16 + 4; // v164
document.getElementById("myDiv").innerHtml = "<span>some stuff</span>" // set custom html into #myDiv
```

###### JS Types
- Available JS types are:

```js
var length = 16; // Number
var lastName = "Johnson"; // String
var cars = [ "Saab", "Volvo", "BMW" ]; // Array
var x = { firstName: "John", lastName: "Doe" }; // Object
var flag = true; // Boolean
```

###### Undefined and Null Types
- `var person; // Undefined (value and type is undefined)`
- `var person = undefined; // Undefined (value and type is undefined)`
- `var person = null; // Null (value is null, type is an object)`
- Undefined vs Null gives the following results:
 - `typeof undefined // undefined`
 - `typeof null // object`
 - `null === undefined // false`
 - `null == undefined // true`

###### NaN Value
- NaN means *not a number*
- Use `isNaN()` function to check if your value is an illegal number

```js
isNaN(5 / 0); // returns false, result = Infinity, typeof = number
isNaN(0 / 0); // returns true, result = NaN, typeof = number
isNaN(true); // returns false, result = true, typeof = boolean
isNaN(""); // returns false, result = "", typeof = string
isNaN("Hello"); // returns true, result = Hello, typeof = string
```

###### JS Arrays
- JS arrays can contain anything you want - `var myArray = ["1", 2, true];`
- Use `myArray.length` property to get array's length

###### Specific Operators
- `typeof` operator - checks data type
- `==` operator - checks value only
- `===` operator - checks value and type

###### Conversion Methods
- `String(123)`, `(123).toString()` - convert numbers to strings
- `String(false)`, `true.toString()` - convert booleans to strings
- `String(Date())`, `Date().toString()` - convert dates to strings
- `Number("3.14")`, `Number("")` - convert strings to numbers
- `parseInt()`, `parseFloat()` - parse strings to numbers

###### Date Object
- There are four ways of instantiating a date:

```js
var d = new Date();
var d = new Date(milliseconds);
var d = new Date(dateString);
var d = new Date(year, month, day, hours, minutes, seconds, milliseconds);
```

- Date object methods
 - `getDate()`, `getYear()`, `getDay()`, `getMonth()`, `getHours()`, `getMinutes()`, `getSeconds()`
 - `setDate()`, `setFullYear()`, `setMonth()`, `setHours()`, `setMinutes()`, `setSeconds()`
 - UTC versions of methods above, etc.

###### Typical Loops
- `for`
- `for-in` (used to go through object properties)
- `while`
- `do-while`

###### JS Events
- Typical events:
 - `onchange`
 - `onclick`
 - `onmouseover`
 - `onmouseout`
 - `onkeydown`
 - `onload`, etc.
- To attach an event:

```js
// 3rd parameter: true - capturing phase, false (default) - bubbling phase
document.getElementById("myDiv").addEventListener("mousemove", myFunction, false);
```

- To remove an event:

```js
document.getElementById("myDiv").removeEventListener("mousemove", myFunction);
```

#### JSON, AJAX

#### JS Regular Expressions

#### Functions, Closures, Objects, Prototypes

#### JS Classes and Modules

#### JS Security

#### JS Performance and Memory Management

#### JS Code Quality

#### JQuery Basics