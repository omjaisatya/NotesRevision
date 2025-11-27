# JavaScript Revision Notes

## Chapter 1. Getting Started with JavaScript

## ECMAScript Version History

| Version     | Release Date |
| ----------- | ------------ |
| 1           | 1997-06-01   |
| 2           | 1998-06-01   |
| 3           | 1998-12-01   |
| E4X         | 2004-06-01   |
| 5           | 2009-12-01   |
| 5.1         | 2011-06-01   |
| 6 (ES2015)  | 2015-06-01   |
| 7 (ES2016)  | 2016-06-14   |
| 8 (ES2017)  | 2017-06-27   |
| 9 (ES2018)  | 2018-06-27   |
| 10 (ES2019) | 2019-06-27   |
| 11 (ES2020) | 2020-06-27   |
| 12 (ES2021) | 2021-06-22   |
| 13 (ES2022) | 2022-06-22   |
| 14 (ES2023) | 2023-06-27   |
| 15 (ES2024) | 2024-06-27   |

# 1.1 Using `console.log()`

### Purpose

Outputs messages to the browser or Node.js console. Used mainly for debugging.

### Basic Usage

```js
console.log("Hello, World!");
```

Returns `undefined` because it has no return value.

### Logging Variables

```js
var foo = "bar";
console.log(foo);
```

### Logging Multiple Values

```js
var a = "first";
var b = "second";
console.log("a:", a, "b:", b);
```

### Placeholders

```js
var greet = "Hello";
var who = "World";
console.log("%s, %s!", greet, who);
```

### Logging Objects

```js
console.log({
  Email: "",
  Groups: {},
  Id: 33,
  IsHiddenInUI: false,
  IsSiteAdmin: false,
  LoginName: "i:0#.w|virtualdomain\\user2",
  PrincipalType: 1,
  Title: "user2",
});
```

### Logging DOM Elements

```js
console.log(document.body);
```

# 1.2 Using the DOM API

### DOM Concept

DOM is an object representation of HTML or XML documents. JavaScript manipulates it via the DOM API.

### Selecting and Editing Elements

HTML:

```html
<p id="paragraph"></p>
```

JavaScript:

```js
document.getElementById("paragraph").textContent = "Hello, World";
```

### Creating Elements Dynamically

```js
var element = document.createElement("p");
element.textContent = "Hello, World";
document.body.appendChild(element);
```

### Timing Requirements

Manipulate DOM only after elements exist. Options:

- Place `<script>` at end of `<body>`.
- Use `window.onload`.
- Wrap code in `setTimeout(..., 0)` to requeue it.

# 1.3 Using `window.alert()`

### Purpose

Displays a modal popup with a message. Blocks user interaction until dismissed.

### Syntax

```js
alert("hello, world");
```

### Notes

- Blocks execution in most browsers.
- Considered poor UX for production.
- Blocked inside iframes in Chrome unless `sandbox="allow-modal"`.

# 1.4 Using `window.prompt()`

### Purpose

Asks user for input via a modal dialog.

### Syntax

```js
prompt(text, defaultValue);
```

### Example

```js
var age = prompt("How old are you?");
console.log(age);
```

### Return Values

- User pressed OK: returns a string.
- User pressed Cancel: returns `null` (Safari returns empty string).

### Notes

- Modal, blocks page interaction.
- Blocked in iframes without `allow-modal`.

# 1.5 Using `window.confirm()`

### Purpose

Displays a modal dialog with OK and Cancel for user confirmation.

### Syntax

```js
var result = window.confirm("Are you sure?");
```

### Typical Use

```js
if (window.confirm("Delete this?")) {
  deleteItem(itemId);
}
```

### Notes

- Returns boolean.
- Same iframe restrictions as `alert` and `prompt`.
- Use sparingly; modal dialogs are intrusive.

# 1.6 DOM API with Graphical Text (Canvas, SVG, Images)

## Using `<canvas>`

### Steps

1. Create a canvas.
2. Set size.
3. Get drawing context.
4. Draw text.
5. Append to page.

### Example

```js
var canvas = document.createElement("canvas");
canvas.width = 500;
canvas.height = 250;

var ctx = canvas.getContext("2d");
ctx.font = "30px Cursive";
ctx.fillText("Hello world!", 50, 50);

document.body.appendChild(canvas);
```

## Using SVG

### Example

```js
var svg = document.createElementNS("http://www.w3.org/2000/svg", "svg");
svg.width = 500;
svg.height = 50;

var text = document.createElementNS("http://www.w3.org/2000/svg", "text");
text.setAttribute("x", "0");
text.setAttribute("y", "50");
text.style.fontFamily = "Times New Roman";
text.style.fontSize = "50";
text.textContent = "Hello world!";

svg.appendChild(text);
document.body.appendChild(svg);
```

## Using an Image File

```js
var img = new Image();
img.src = "https://i.ytimg.com/vi/zecueq-mo4M/maxresdefault.jpg";
document.body.appendChild(img);
```

## Chapter 2. JavaScript Variables

## Overview

A variable stores a value that can be referenced and manipulated later.

- **variable_name**: identifier for the variable
- **=**: assignment operator
- **value**: assigned data. If no value is assigned, the variable is `undefined`

JavaScript variables can store any data type because JS uses dynamic typing.

## 2.1 Defining a Variable

### Example

```js
var myVariable = "This is a variable!";
```

This creates a variable using `var` and assigns a string.
A string is text data enclosed in quotes.

## 2.2 Using a Variable

### Reassigning Values

```js
var number1 = 5;
number1 = 3;
```

### Viewing the Value

```js
console.log(number1); // 3
alert(number1); // 3
```

### Basic Arithmetic

```js
number1 = number1 + 5; // 8
number1 = number1 - 6; // 2

var number2 = number1 * 10; // 20
var number3 = number2 / number1; // 10
```

### String Concatenation

```js
var myString = "I am a " + "string!";
// "I am a string!"
```

## 2.3 Types of Variables

### Important Correction

JavaScript does not have separate `integer`, `float`, `double`, or `long` types.
There is **one** number type: **Number** (64-bit floating point).
The examples below are still valid JS, but the comments in the original text were factually wrong.

### Valid Examples

```js
var myInteger = 12;
var myLong = 9310141419482;
var myFloat = 5.5;
var myDouble = 9310141419482.22;
```

All of these are the same type internally: **Number**.

### Other Primitive Types

```js
var myBoolean = true;
var myBoolean2 = false;

var myNotANumber = NaN;
var NaN_Example = 0 / 0; // NaN

var notDefined; // undefined (no value assigned)

var myNull = null; // intentional absence of value
```

### Undefined example

```js
alert(aRandomVariable); // undefined
```

## 2.4 Arrays and Objects

## Arrays

An array stores ordered values accessed by index.

```js
var myArray = []; // empty array

var favoriteFruits = ["apple", "orange", "strawberry"];
var carsInParkingLot = ["Toyota", "Ferrari", "Lexus"];
var employees = ["Billy", "Bob", "Joe"];
var primeNumbers = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29, 31];
var randomVariables = [2, "any type works", undefined, null, true, 2.51];
```

### Accessing Elements

```js
myArray = ["zero", "one", "two"];
alert(myArray[0]); // "zero"

myArray = ["John Doe", "Billy"];
var elementNumber = 1;
alert(myArray[elementNumber]); // "Billy"
```

## Objects

Objects store key-value pairs, offering meaningful property names instead of numeric indexes.

```js
var myObject = {};

var john = {
  firstname: "John",
  lastname: "Doe",
  fullname: "John Doe",
};

var billy = {
  firstname: "Billy",
  lastname: undefined,
  fullname: "Billy",
};
```

### Accessing Object Properties

```js
alert(john.fullname); // "John Doe"
alert(billy.firstname); // "Billy"
```

### Why objects are better than arrays here

Instead of:

```js
["John Doe", "Billy"][0];
```

You get readable access:

```js
john.fullname;
billy.fullname;
```

Clearer, scalable, and maintainable.
