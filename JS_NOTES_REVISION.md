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

# Chapter 2. JavaScript Variables

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

## Chapter 3. Built-in Constants

# 3.1 null

### What null Represents

- `null` is a primitive value meaning **intentional absence of any object value**.
- It is **not** the same as `undefined`, although they are loosely equal.

### Comparisons

```js
null == undefined; // true  (loose equality)
null === undefined; // false (strict equality)
```

### typeof Quirk

```js
typeof null; // "object" (this is a long-standing bug in JS)
```

### Proper Check

```js
var a = null;
a === null; // true
```

# 3.2 Testing for NaN with isNaN()

### window.isNaN()

`isNaN()` attempts to convert the input to a number first, then checks if the result is `NaN`.
This implicit conversion causes unintuitive results.

### Examples

```js
isNaN(NaN); // true
isNaN(1); // false
isNaN(-2e-4); // false
isNaN(Infinity); // false

isNaN(true); // false (becomes 1)
isNaN(false); // false (becomes 0)
isNaN(null); // false (becomes 0)
isNaN(""); // false (becomes 0)
isNaN("45.3"); // false
isNaN("10$"); // true
isNaN("hello"); // true
isNaN(undefined); // true
isNaN(); // true (implicitly undefined)
isNaN({}); // true
isNaN(function () {}); // true
isNaN([1, 2]); // true (becomes "1,2")
```

### Arrays Specifically

`Number([])` → `0`
`Number([34])` → `34`
`Number([1,2])` → `NaN`

So:

```js
isNaN([]); // false
isNaN([34]); // false
isNaN([1, 2]); // true
```

## ES6+ Number.isNaN()

### Purpose

Fixes the flaws of `isNaN()` by **not converting** the value before checking.

### Rules

- Only `Number.isNaN(NaN)` returns `true`.
- Anything that is not a number returns `false`.

### Examples

```js
Number.isNaN(NaN); // true

Number.isNaN(1); // false
Number.isNaN("hello"); // false
Number.isNaN(undefined); // false
Number.isNaN([1, 2]); // false
Number.isNaN("10$"); // false
```

# 3.3 NaN

### Meaning

**NaN** stands for “Not a Number”.
Returned when a numeric operation cannot produce a valid number.

### Properties

```js
typeof NaN; // "number"
NaN === NaN; // false
NaN == NaN; // false
```

### Global Binding

```js
window.hasOwnProperty("NaN"); // true
```

### Never compare NaN using == or ===

Use:

```js
Number.isNaN(value);
```

# 3.4 undefined and null

### undefined

Represents the **absence of an assigned value**. It means "no value was provided".

### null

Represents the **intentional** absence of value.

### typeof

```js
typeof undefined; // "undefined"
typeof null; // "object" (quirk)
```

## When undefined appears

### 1. Declared but not assigned

```js
let foo;
foo; // undefined
```

### 2. Accessing non-existing object properties

```js
let obj = { a: "a" };
obj.b; // undefined
```

### 3. Function with no return

```js
function test() {}
test(); // undefined
```

### 4. Missing arguments

```js
function f(x) {
  return x;
}
f(); // undefined
```

### Global undefined

```js
window.undefined; // undefined
window.hasOwnProperty("undefined"); // true
```

### Pre-ES5 quirk

`undefined` used to be writable. Now it is read-only.

# 3.5 Infinity and -Infinity

### Meaning

Represents mathematical positive or negative infinity.

```js
1 / 0; // Infinity
1 / -0; // -Infinity
```

### Properties

```js
Infinity === Number.POSITIVE_INFINITY; // true
-Infinity === Number.NEGATIVE_INFINITY; // true
```

### Examples

```js
Infinity > 1e308; // true
23 / Infinity; // 0

var a = 0,
  b = -0;
a === b; // true
1 / a === 1 / b; // false (Infinity vs -Infinity)
```

# 3.6 Number Constants

### Useful Number Constants

```js
Number.MAX_VALUE; // 1.7976931348623157e+308
Number.MIN_VALUE; // 5e-324

Number.MAX_SAFE_INTEGER; // 9007199254740991
Number.MIN_SAFE_INTEGER; // -9007199254740991

Number.EPSILON; // 2.220446049250313e-16

Number.POSITIVE_INFINITY; // Infinity
Number.NEGATIVE_INFINITY; // -Infinity
Number.NaN; // NaN
```

### Notes

- Operations outside the safe integer range may produce inaccurate results.
- `Number.EPSILON` is useful for floating-point comparison.

# 3.7 Operations that Return NaN

### NaN occurs when math operations use invalid numeric operands.

Examples:

```js
"b" * 3; // NaN
"cde" - "e"; // NaN
[1, 2, 3] * 2; // NaN
```

### Exception: Single-element arrays

```js
[2] * [3]; // 6 (both converted to numbers)
```

### Remember

`+` with strings concatenates:

```js
"a" + "b"; // "ab"
```

### Zero divided by zero

```js
0 / 0; // NaN
```

# 3.8 Math Functions that Return NaN

### Non-numeric Input

```js
Math.floor("a"); // NaN
```

### Invalid Domain Input

Square root of a negative number:

```js
Math.sqrt(-1); // NaN
```

# Chapter 4. Comments

# 4.1 Using Comments

Comments allow you to annotate code, explain logic, disable execution, or leave reminders. JavaScript supports two native comment styles.

## Single-line Comments (`//`)

Everything after `//` on the same line is ignored by the JavaScript engine.

```js
function elementAt(event) {
  // Gets the element at the event's coordinates
  return document.elementFromPoint(event.clientX, event.clientY);
}

// TODO: write more cool stuff!
```

## Multi-line Comments (`/* ... */`)

Everything between `/*` and `*/` is ignored, even across multiple lines.

```js
/*
Gets the element from Event coordinates.
Usage:
var clickedEl = someEl.addEventListener("click", elementAt, false);
*/
function elementAt(event) {
  return document.elementFromPoint(event.clientX, event.clientY);
}

/* TODO: write more useful comments! */
```

Use multi-line comments for blocks of explanation, documentation, or temporarily disabling multiple lines.

# 4.2 HTML Comments in JavaScript (Bad Practice)

Historically, HTML comments were sometimes used in JavaScript for compatibility with ancient browsers. Modern JavaScript should **never** rely on this.

## HTML-style Opening Comment (`<!--`)

If used at the beginning of a JavaScript line, the JS engine treats it as a comment starter.
The closing `-->` is ignored by JavaScript.

```js
<!-- A single-line comment
<!-- --> Same effect as //
```

This behavior exists for backward compatibility and should not be used today.

## Legacy Example: Hiding JS from Non-JS Browsers

Old browsers that didn’t understand `<script>` tags would display JavaScript as text. Developers hid the JS using HTML comment markers:

```html
<script type="text/javascript">
  <!--
  // JavaScript code here
  // -->
</script>
```

This is obsolete and should never appear in modern code.

## Using `-->` at Line Start in JavaScript

If a line begins with `-->`, JavaScript ignores everything after it:

```js
--> unreachable JS code
```

Again, this is outdated behavior.

# HTML–JavaScript Hybrid Exploit (For Understanding Only)

Because HTML comments and JS comments behave differently, developers once used them to create files that could be interpreted as HTML or JavaScript depending on context.

Example:

```js
<!--
self.postMessage('reached JS "file"');
/*
-->
<!DOCTYPE html>
<script>
  var w1 = new Worker('#1');
  w1.onmessage = function(e) {
    console.log(e.data); // 'reached JS "file"'
  };
</script>
<!--
*/
-->
```

### What happens:

- When parsed as **HTML**, everything between `<!--` and `-->` is treated as an HTML comment and ignored.
- When parsed as **JavaScript**, only lines beginning with `<!--` or `-->` are ignored.
  JavaScript continues reading subsequent lines until it hits standard JS comment syntax (`/* ... */`).

This is purely historical, not something you should ever write.

# Chapter 5. Console

The browser (and Node) debugging console exposes a `console` object with many utility methods for logging, timing, grouping, inspecting, and debugging runtime behavior. Behavior and available methods vary by environment and browser, so use feature checks when needed.

## Common `console` methods

Typical methods you will see (not exhaustive and may differ by runtime):

```
assert, clear, count, debug, dir, dirxml, error, group, groupCollapsed,
groupEnd, info, log, table, time, timeEnd, timeStamp, trace, warn
```

Note: Chrome exposes additional internals like `console.memory`. Never rely on non-standard features in production.

## Opening the Console (quick shortcuts)

- **Chrome**

  - Windows / Linux: `Ctrl + Shift + J` or `F12` then Console tab
  - macOS: `Cmd + Option + J`

- **Firefox**

  - Windows / Linux: `Ctrl + Shift + K` or `F12` then Console tab
  - macOS: `Cmd + Option + K`

- **Edge / IE**

  - `F12` then Console tab

- **Safari**

  - Enable Develop menu in Preferences, then `Develop → Show Error Console` or `⌘ + Option + C`

- **Opera**

  - `Ctrl + Shift + I` then Console tab

## Compatibility & defensive patterns

In old IE versions (and some limited environments) `console` may be undefined unless dev tools are open. Prevent fatal errors with a guard or shim:

```js
// Guard before using:
if (typeof window.console !== "undefined") {
  console.log("Hello World");
}

// Lightweight shim (silences all logs)
if (!window.console) {
  console = { log() {} };
}
```

The shim stops all console output; extend it if you need methods like `dir`, `warn`, etc.

## 5.1 Measuring time `console.time()` / `console.timeEnd()`

Start/stop timers by a `label`. Multiple `timeEnd()` calls with the same label report elapsed time since the original `time()`.

```js
console.time("response in");
/* do work */
console.timeEnd("response in"); // response in: 123.456ms
```

You can call `timeEnd('label')` repeatedly to get successive elapsed times since the `time('label')` call.

Example: profiling nested loops or async response times.

## 5.2 Formatting console output

`console` supports printf-like tokens:

- `%s` → string
- `%i` or `%d` → integer
- `%f` → floating point
- `%o` → expandable DOM element
- `%O` → expandable JavaScript object
- `%c` → apply CSS to text (Chrome/Chromium-based consoles)

```js
console.log("%s has %d points", "Sam", 100);
console.log("%o", document.body);
console.log("%cHello world!", "color: blue; font-size: 16px");
```

`%c` accepts multiple occurrences; each `%c` consumes one CSS argument.

**Caveat:** styling is purely cosmetic in devtools and not portable to all consoles.

## 5.3 Groups `console.group()`, `console.groupCollapsed()`, `console.groupEnd()`

Indent and collapse related logs:

```js
console.group("Init");
console.log("step 1");
console.groupCollapsed("subgroup");
console.log("sub step");
console.groupEnd();
console.groupEnd();
```

`groupCollapsed` starts collapsed; `group` starts expanded. Use groups to keep console output readable.

## 5.4 Basic logging and variants

- `console.log(...)` — general logging, accepts multiple args
- `console.info(...)` — informational (may show an icon)
- `console.warn(...)` — warnings (often highlighted)
- `console.error(...)` — errors (often red or treated specially)

All accept objects, arrays, functions, Dates, etc. Many consoles allow expanding object trees interactively.

**Tip:** remove or guard verbose logs in production builds.

## 5.5 Stack traces `console.trace()`

Prints the current stack trace (useful to see call paths):

```js
function a() {
  b();
}
function b() {
  console.trace("trace here");
}
a();
```

You can also inspect `new Error().stack` for programmatic access.

## 5.6 Tabular output `console.table()`

Displays arrays or objects as a table, optionally restricting columns:

```js
console.table(["Hello", "world"]);
// or
console.table({ foo: "bar", bar: "baz" });
// array of objects with selected columns:
console.table(personArr, ["name", "personId"]);
```

Useful for quick inspection of homogeneous collections.

## 5.7 Counting `console.count([label])`

Keeps an internal counter per label and logs `label: X`. Useful for seeing how often code paths execute.

```js
console.count("loop");
// => loop: 1
console.count("loop");
// => loop: 2
console.count(); // uses empty string label
```

Note: the label normalization rules vary by engine (`Number('42.3')` vs `'42.3'` may produce same label in some consoles).

## 5.8 Clearing the console `console.clear()`

Clears the console output. Some environments print a small marker like "Console was cleared".

```js
console.clear();
```

## 5.9 Inspecting objects `console.dir()` and `console.dirxml()`

- `console.dir(obj)` — shows a navigable list of object properties (often better for plain JS objects).
- `console.dirxml(node)` — prints an XML/HTML-like representation for DOM nodes; otherwise prints object representation.

```js
console.dir({ foo: { bar: "data" } });
console.dirxml(document);
```

Behavior differs across browsers; try both when inspecting complex structures.

## 5.10 Assertions `console.assert()`

Logs an error message if the assertion expression is falsy. It does not throw (in browsers) so execution continues.

```js
console.assert(1 === 2, "this should never happen");
```

Additional arguments after the assertion are printed only when the assertion fails.

**Caveat:** `console.assert` is not a replacement for test-framework assertions since it usually won’t stop execution. Node.js throws an `AssertionError` only in that environment.

## Practical tips & best practices

- Avoid leaving verbose `console.log` calls in production code. Use build tools to strip them or guard with environment checks.
- Prefer `console.error()` for error conditions and `console.warn()` for recoverable issues.
- Use `console.time()`/`timeEnd()` for quick performance checks; use dedicated profilers for deeper analysis.
- Use `console.table()` for readable tabular data.
- Wrap console usage with feature checks when supporting legacy environments.
- Know that consoles are developer tools — formatting and features are implementation-specific; write code that doesn’t depend on console side-effects.

# Chapter 6. Datatypes in JavaScript

JavaScript's type system is flexible but full of quirks. This chapter summarizes the correct, practical ways to inspect and understand values.

## 6.1 `typeof`

`typeof` is the built-in operator for checking the type of a value. It works well for primitives but is inconsistent for some objects.

### Results

#### 1. Strings

```js
typeof "String"; // "string"
typeof Date(2011, 1, 1); // "string" because Date() without new returns a string
```

#### 2. Numbers

```js
typeof 42; // "number"
```

#### 3. Boolean

```js
typeof true; // "boolean"
```

#### 4. Object (overly broad)

```js
typeof {}; // "object"
typeof []; // "object"
typeof null; // "object"       // historical bug
typeof /aaa/; // "object"
typeof Error(); // "object"
```

#### 5. Function

```js
typeof function () {}; // "function"
```

#### 6. Undefined

```js
var x;
typeof x; // "undefined"
```

### Key issue

`typeof` lumps many different object categories into `"object"` and incorrectly reports `null` as `"object"`.

## 6.2 Finding an Object’s Class (`instanceof` and `constructor`)

### Using `instanceof`

Use `instanceof` to check whether an object was created by a constructor or its prototype chain.

```js
function sum(...args) {
  if (args.length === 1) {
    const [first] = args;
    if (first instanceof Array) {
      return sum(...first);
    }
  }
  return args.reduce((a, b) => a + b);
}

console.log(sum(1, 2, 3)); // 6
console.log(sum([1, 2, 3])); // 6
console.log(sum(4)); // 4
```

### Primitive caveat

Primitives are **not** instances of wrapper constructors:

```js
2 instanceof Number; // false
"abc" instanceof String; // false
true instanceof Boolean; // false
Symbol() instanceof Symbol; // false
```

### Using `.constructor`

Every value except `null` and `undefined` has a `.constructor` reference:

```js
[].constructor === Array; // true
[].constructor === Object; // false
```

This does not check inheritance, unlike `instanceof`.

### Safe example function:

```js
function isNumber(value) {
  if (value === null || value === undefined) return false;
  return value.constructor === Number;
}

isNumber(null); // false
isNumber("abc"); // false
isNumber(0); // true
isNumber(Number("10")); // true
isNumber(NaN); // true
```

## 6.3 Getting Object Type with `Object.prototype.toString.call()`

This is the **most reliable** way to get the internal `[[Class]]` of a value.
It returns strings like `"[object Array]"`.

### Examples

#### 1. String

```js
Object.prototype.toString.call("String");
// "[object String]"
```

#### 2. Number

```js
Object.prototype.toString.call(42);
// "[object Number]"
```

#### 3. Boolean

```js
Object.prototype.toString.call(true);
// "[object Boolean]"
```

#### 4. Object

```js
Object.prototype.toString.call({});
// "[object Object]"
```

#### 5. Function

```js
Object.prototype.toString.call(function () {});
// "[object Function]"
```

#### 6. Date

```js
Object.prototype.toString.call(new Date());
// "[object Date]"
```

#### 7. RegExp

```js
Object.prototype.toString.call(/foo/);
// "[object RegExp]"
```

#### 8. Array

```js
Object.prototype.toString.call([]);
// "[object Array]"
```

#### 9. Null

```js
Object.prototype.toString.call(null);
// "[object Null]"
```

#### 10. Undefined

```js
Object.prototype.toString.call(undefined);
// "[object Undefined]"
```

#### 11. Error

```js
Object.prototype.toString.call(Error());
// "[object Error]"
```

## Summary of Type-Checking Methods

| Method                           | Good for                             | Weaknesses                                         |
| -------------------------------- | ------------------------------------ | -------------------------------------------------- |
| `typeof`                         | Primitives, functions                | `null` bug, arrays/objects indistinguishable       |
| `instanceof`                     | Object instances, inheritance checks | Fails with primitives, problems across iframes     |
| `.constructor`                   | Direct constructor equality          | Cannot detect subclasses, fails for null/undefined |
| `Object.prototype.toString.call` | Precise internal class               | Verbose, not widely known by beginners             |

This is the hierarchy you should fall back on when accuracy matters.

# Chapter 7. Strings

Comprehensive, practical summary of string handling in JavaScript. Includes modern (ES6+) approaches and important edge-case warnings.

## 7.1 Basic info and creation

- Strings may be written with single quotes, double quotes, or backticks (template literals).

```js
let s1 = "Hello";
let s2 = "world";
let s3 = `Hello World`; // template literal (ES2015+)
```

- Convert values to strings:

```js
String(32); // "32"
(5232).toString(); // "5232"
false.toString(); // "false"
String.fromCharCode(104, 101, 108, 108, 111); // "hello"
```

- **Avoid** `new String("...")` that creates a `String` object (type "object") instead of a primitive string:

```js
let objString = new String("hi");
typeof objString; // "object"
typeof objString.valueOf(); // "string"
```

- Strings are **immutable**. Methods return new strings.

## 7.1.1 Concatenation

- `+` operator:

```js
"Foo" + "Bar"; // "FooBar"
"Foo" + " " + "Bar"; // "Foo Bar"
"string" + 32 + true; // "string32true"
```

- `.concat()`:

```js
"Foo".concat("Bar"); // "FooBar"
```

## 7.1.2 Template literals (ES6+)

- Interpolation and multi-line strings:

```js
let place = `World`;
let greet = `Hello ${place}!`; // "Hello World!"
```

- `String.raw` preserves backslashes:

```js
`a\\b`; // "a\b"
String.raw`a\\b`; // "a\\b"
```

## 7.2 Reversing strings - pitfalls & approaches

### Naive approach (works for BMP-only strings)

```js
function reverseString(str) {
  return str.split("").reverse().join("");
}
```

**Problem:** fails for surrogate pairs and combining marks (emoji, many non-Latin scripts).

### Safer modern approaches

- Using spread or `Array.from` (better with Unicode code points):

```js
[...String(str)].reverse().join("");
Array.from(str).reverse().join("");
```

These handle many astral symbols correctly because they operate on user-perceived characters rather than UTF-16 code units.

### Manual approach

```js
function reverseLoop(s) {
  let r = "";
  for (let i = s.length - 1; i >= 0; i--) r += s[i];
  return r;
}
```

Still subject to surrogate/combining-mark issues.

## 7.3 Comparing strings (lexicographic)

- `localeCompare()` recommended for locale-aware comparisons:

```js
"hello".localeCompare("world"); // negative
```

- Simple comparator for sorting (non-locale-sensitive):

```js
function strcmp(a, b) {
  if (a === b) return 0;
  return a > b ? 1 : -1;
}
arr.sort((a, b) => a.localeCompare(b));
```

## 7.4 Accessing characters

- `charAt(index)` and bracket indexing:

```js
let s = "Hello";
s.charAt(4); // "o"
s[4]; // "o"
```

- `charCodeAt(index)` returns UTF-16 code unit value:

```js
"Hello".charCodeAt(4); // 111
```

- For full Unicode code points (astral characters) use `codePointAt` (ES6+):

```js
"😀".codePointAt(0); // 128512
```

## 7.5 Escaping quotes

- Escape using backslash:

```js
let a = "L'albero";
let b = 'I feel "high"';
```

- Use template literals to avoid many escapes:

```js
let t = `He said "it's fine"`;
```

- When embedding HTML, you may also use entities `&apos;` and `&quot;` as appropriate.

## 7.6 Word/character/line counter (example)

```js
function wordCount(val) {
  const words = val.match(/\S+/g);
  return {
    charactersNoSpaces: val.replace(/\s+/g, "").length,
    characters: val.length,
    words: words ? words.length : 0,
    lines: val.split(/\r*\n/).length,
  };
}
```

## 7.7 Trimming whitespace

- Standard:

```js
"  hello  ".trim(); // "hello"
```

- Variants (some engines polyfilled until standardization):

```js
" this ".trimStart(); // "this "
" this ".trimEnd(); // " this"
```

## 7.8 Splitting and joining

```js
let s = "one, two, three";
s.split(", "); // ["one", "two", "three"]
s.split(", ").join("--"); // "one--two--three"
```

## 7.9 Unicode

- JavaScript strings are sequences of UTF-16 code units representing Unicode text.
- `charCodeAt` returns a UTF-16 code unit. For code points beyond BMP, use `codePointAt` and iterate with `for...of`, `Array.from`, or spread (`[...str]`).

## 7.10 Detecting a string

- Primitive string:

```js
typeof value === "string";
```

- String object:

```js
value instanceof String;
```

- Combined helper:

```js
function isString(v) {
  return typeof v === "string" || v instanceof String;
}
```

- Or use `Object.prototype.toString.call(v) === "[object String]"` for robustness.

## 7.11 Substrings with `slice`

```js
let s = "0123456789abcdefg";
s.slice(0, 5); // "01234"
s.slice(10); // "abcdefg"
```

`slice` accepts negative indices.

## 7.12 Character codes vs code points

- `charCodeAt(index)` → UTF-16 code unit (0–65535).
- `codePointAt(index)` → full Unicode code point (ES6+), required for astral characters.

## 7.13 Number ⇄ String conversions (radix)

- `num.toString(radix)` converts to base 2–36:

```js
(12).toString(16); // "c"
```

- `parseInt(str, radix)` parses back:

```js
parseInt("c", 16); // 12
```

- For fractional conversions between bases, split integer and fraction parts and convert accordingly (careful with floating-point precision).

## 7.14 Find and replace

- `indexOf`, `lastIndexOf`, `includes`:

```js
"Hello".indexOf("l"); // 2
"Hello".lastIndexOf("l"); // 3
"Hello".includes("ll"); // true
```

- `replace` (does not mutate original string):

```js
let s = "Hello, World!";
s.replace("Hello", "Bye"); // "Bye, World!"
s.replace(/W.{3}d/g, "Universe"); // "Bye, Universe!"
```

- `replace` with function for dynamic replacements (capture groups passed to replacer).

## 7.15 Index of substring with start position

```js
"Hellow World".indexOf("Wor"); // 7
"harr dee harr dee harr".indexOf("dee", 10); // 14
```

`indexOf` is case-sensitive.

## 7.16 / 7.17 Case conversion

```js
"qwerty".toUpperCase(); // "QWERTY"
"QWERTY".toLowerCase(); // "qwerty"
```

## 7.18 Repeating strings

- ES6:

```js
"abc".repeat(3); // "abcabcabc"
"abc".repeat(0); // ""
// "abc".repeat(-1); // RangeError
```

- Pre-ES6 common idiom:

```js
new Array(n + 1).join("abc");
```

(Prefer `repeat` or a polyfill for clarity.)

# Chapter 8. Date

Compact, accurate reference for working with `Date` in JavaScript. Covers creation, formatting, UTC vs local, common pitfalls, and handy utilities.

## Parameter summary (when using `new Date(year, month, ...)`)

- `value` —> milliseconds since Unix epoch (1970-01-01T00:00:00.000Z)
- `dateAsString` —> parseable date string (see `Date.parse`)
- `year` —> full year (but values `0..99` are treated specially; see note)
- `month` —> `0..11` (`0` = January, `11` = December)
- `day` —> day of month `1..31` (optional)
- `hour` —> `0..23` (optional)
- `minute` —> `0..59` (optional)
- `second` —> `0..59` (optional)
- `millisecond` —> `0..999` (optional)

**Important:** out-of-range values roll over (e.g., month `12` → next January, day `32` → next month). No error is thrown.

## 8.1 Creating `Date` objects

### No arguments

```js
new Date(); // current date/time (local)
```

### One numeric argument (milliseconds since epoch)

```js
new Date(0); // 1970-01-01T00:00:00.000Z
new Date(749019369738); // date at given ms
```

### One string argument (parsed)

```js
new Date("2012-01-01T00:00:00.000Z"); // ISO — parsed as UTC
new Date("11/12/2012"); // implementation-dependent parsing — avoid non-ISO strings
```

### Multiple numeric args (year, month, day, hours, minutes, seconds, ms)

```js
new Date(2017, 5, 1); // June 1, 2017 (month is 0-based)
```

### Create from UTC values

```js
new Date(Date.UTC(2012, 0, 1)); // constructs a Date for 2012-01-01T00:00:00Z
```

### Special: years `0..99`

Values `0..99` are interpreted as `1900..1999` when passed to the multi-arg constructor. Use `setFullYear()` to set year 12 CE:

```js
let d = new Date(12, 0); // 1912-01-01
d.setFullYear(12); // year 12 CE
```

## 8.2 Converting `Date` to string

- `date.toString()` → human-local string, e.g. `"Fri Apr 15 2016 07:48:48 GMT-0400 (EDT)"`
- `date.toTimeString()` → time part with zone
- `date.toDateString()` → date part only
- `date.toUTCString()` → UTC string, e.g. `"Fri, 15 Apr 2016 11:48:48 GMT"`
- `date.toISOString()` → ISO 8601 in UTC, e.g. `"2016-04-14T23:49:08.596Z"`
- `date.toGMTString()` → deprecated; prefer `toUTCString()`

## 8.3 UTC vs Local time — best practices

- **Local `new Date(...)`** creates date in local timezone. This can cause surprising differences when communicating plain day/month/year across timezones.
- **Prefer UTC** for timezone-agnostic dates: construct with `Date.UTC(...)` or use UTC getter/setter methods.

```js
// Communicate a calendar date unambiguously
let birthdayUtcMs = Date.UTC(2000, 0, 1); // milliseconds for 2000-01-01T00:00:00Z
// On receiver:
let birthday = new Date(birthdayUtcMs);
```

- Use `getUTCFullYear()`, `getUTCMonth()`, `getUTCDate()`, etc., when interpreting UTC-based timestamps.
- `Date.UTC(...)` returns epoch ms and is useful for transport: `new Date(Date.UTC(...))` or send ms directly.

## UTC setter/getter counterparts

- Local: `getFullYear(), getMonth(), getDate(), getHours(), getMinutes(), getSeconds(), getMilliseconds()`
- UTC: `getUTCFullYear(), getUTCMonth(), getUTCDate(), getUTCHours(), ...`
- Setters: `setFullYear()`, `setMonth()`, `setDate()`, `setHours()`, plus `setUTCFullYear()`, `setUTCMonth()`, etc.

## 8.4 Formatting dates (localization)

Use `toLocaleDateString` / `toLocaleString` / `toLocaleTimeString` with options:

```js
let opts = { weekday: "long", year: "numeric", month: "short", day: "numeric" };
new Date().toLocaleDateString("en-GB", opts); // "Thursday, Apr 14, 2016" (locale-dependent)
```

`locales` accepts BCP 47 tags (e.g., `'en-GB'`). `options` supports `timeZone`, `year`, `month`, `day`, `hour`, `minute`, `second`, `weekday`, `timeZoneName`, `hour12`, and more.

If you need highly custom formatting, build a small formatter using getters (or use a date library).

## 8.5 Milliseconds since epoch

- Static now:

```js
Date.now(); // ms since 1970-01-01T00:00:00Z
```

- Instance:

```js
new Date().getTime();
```

Use epoch ms for unambiguous transport/storage.

## 8.6 Common getters (current values)

```js
new Date().getFullYear(); // 4-digit year
new Date().getMonth(); // 0-11 (add 1 for human month)
new Date().getDate(); // day of month 1-31
new Date().getHours(); // 0-23
new Date().getMinutes(); // 0-59
new Date().getSeconds(); // 0-59
new Date().getMilliseconds(); // 0-999
```

## 8.7 Incrementing a date

Rollover works automatically with setter/getter arithmetic:

```js
let d = new Date();
d.setDate(d.getDate() + 1); // add one day
```

Adding more than the days in a month rolls into subsequent months. Same behavior applies for `setMonth`, `setHours`, etc.

### Add business days (example)

```js
function addWorkDays(startDate, days) {
  let dow = startDate.getDay(); // 0..6
  let daysToAdd = days;
  if (dow === 0) daysToAdd++; // if Sunday, skip to Monday
  if (dow + daysToAdd >= 6) {
    let remaining = daysToAdd - (5 - dow);
    daysToAdd += 2; // add weekend
    if (remaining > 5) {
      daysToAdd += 2 * Math.floor(remaining / 5);
      if (remaining % 5 === 0) daysToAdd -= 2;
    }
  }
  startDate.setDate(startDate.getDate() + daysToAdd);
  return startDate;
}
```

Note: Holidays are not handled.

## 8.8 Convert `Date` to JSON

- `date.toJSON()` → returns `date.toISOString()` by default, e.g. `"2016-04-14T23:49:08.596Z"`

This ISO string is suitable for APIs and storage.

# Chapter 9. Date Comparison

Practical, accurate notes for comparing `Date` objects and computing differences. Includes examples, common pitfalls, and handy helper functions.

## 9.1 Comparing Date values

### Key idea

`Date` objects are objects. Using `==` or `===` compares **references**, not the point-in-time they represent. To compare the actual time value, compare their numeric timestamps.

`Date.prototype.valueOf()` and `Date.prototype.getTime()` both return the epoch milliseconds for the `Date` instance and are interchangeable.

### Examples

```js
const d1 = new Date();
const d2 = new Date(d1.valueOf() + 10);

d1 === d2; // false (different objects)
d1.valueOf() === d2.getTime(); // false (compares timestamps)
d1 < d2; // true  (works because both are coerced to numbers)
d1 <= d2; // true  (works with equality)
```

If two variables reference the same object, `===` returns `true`:

```js
const a = new Date();
const b = a;
a === b; // true
```

### Correct equality check (same instant in time)

```js
function isSameMoment(a, b) {
  return a?.valueOf() === b?.valueOf(); // safe if a or b might be null/undefined
}

isSameMoment(new Date(0), new Date(0)); // true
```

## 9.2 Date difference calculation

Compute differences by subtracting timestamps (ms). Convert milliseconds into desired units.

### Milliseconds, seconds, minutes, hours, days, years

```js
const date1 = new Date();
const date2 = new Date(date1.valueOf() + 5_000); // +5 seconds

const diffMs = date2.getTime() - date1.getTime(); // 5000
const diffSec = diffMs / 1000; // 5
const diffMin = diffSec / 60;
const diffHours = diffMin / 60;
const diffDays = diffHours / 24;
const diffYears = diffDays / 365; // approximate
```

### Practical helper functions

```js
// returns difference in milliseconds (positive if b > a)
function diffMs(a, b) {
  return b.getTime() - a.getTime();
}

// difference in whole days (floor)
function diffDays(a, b) {
  return Math.floor(diffMs(a, b) / (1000 * 60 * 60 * 24));
}

// difference in hours with fraction
function diffHours(a, b) {
  return diffMs(a, b) / (1000 * 60 * 60);
}

// formatted breakdown: days, hours, minutes, seconds
function diffHuman(a, b) {
  let ms = Math.abs(diffMs(a, b));
  const days = Math.floor(ms / 86400000);
  ms %= 86400000;
  const hours = Math.floor(ms / 3600000);
  ms %= 3600000;
  const minutes = Math.floor(ms / 60000);
  ms %= 60000;
  const seconds = Math.floor(ms / 1000);
  ms %= 1000;
  return { days, hours, minutes, seconds, milliseconds: ms };
}
```

## 9.3 Important caveats & gotchas

- **Reference vs value:** `===` compares object identity. Use `getTime()`/`valueOf()` for timestamp equality.
- **Time zones:** `Date` stores a point in time (epoch ms). `getFullYear()`/`getMonth()`/`getDate()` return local-time components. When comparing calendar dates from different time zones, convert to UTC or compare normalized date-only values.
- **Daylight saving time (DST):** Adding 24 hours (ms) may not always move the local date by +1 day if DST boundary occurs. Use date setters (`setDate(getDate() + N)`) when you mean "advance calendar day" in local time.
- **Leap years and varying month lengths:** Converting `diffMs / (1000*60*60*24*365)` gives only an approximation for years. For accurate year/month differences, compute with calendar arithmetic (compare year/month/day components) or use a library.
- **Floating point rounding:** Large differences divided by units can produce fractional imprecision; round appropriately when displaying.
- **Null/undefined inputs:** Guard against invalid inputs before calling `.getTime()`.

## 9.4 Examples for common tasks

### Are two dates on the same calendar day (local time)?

```js
function isSameLocalDay(a, b) {
  return (
    a.getFullYear() === b.getFullYear() &&
    a.getMonth() === b.getMonth() &&
    a.getDate() === b.getDate()
  );
}
```

### Are two dates on the same UTC day?

```js
function isSameUtcDay(a, b) {
  return (
    a.getUTCFullYear() === b.getUTCFullYear() &&
    a.getUTCMonth() === b.getUTCMonth() &&
    a.getUTCDate() === b.getUTCDate()
  );
}
```

### Number of whole days between two dates (calendar-aware)

If you want the difference in calendar days regardless of DST shifts, normalize both to midnight local time:

```js
function daysBetweenCalendar(a, b) {
  const ad = new Date(a.getFullYear(), a.getMonth(), a.getDate());
  const bd = new Date(b.getFullYear(), b.getMonth(), b.getDate());
  return Math.round((bd - ad) / (1000 * 60 * 60 * 24));
}
```

## 9.5 Validity checks

Always verify inputs:

```js
function isValidDate(d) {
  return d instanceof Date && !Number.isNaN(d.getTime());
}
```

# Chapter 10. Comparison Operations

Clear, practical summary of equality, relational operators, coercion rules, short-circuiting, and useful patterns. Focus on what trips people up and how to avoid bugs.

## 10.1 Abstract equality (`==`) and coercion - the problem

`==` performs type conversion when operand types differ. That coercion produces surprising results:

```js
"" == 0; // true
0 == "0"; // true
"" == "0"; // false

false == 0; // true
false == "0"; // true
```

Why? `""` converts to `0`, `"0"` converts to `0`, `false` converts to `0`. But comparing two strings does no conversion, so `"" == "0"` is false.

**Rule of thumb:** avoid `==` unless you understand the coercion rules. Prefer explicit conversions or `===`.

```js
Number("") === 0; // true
String(0) === "0"; // true
```

## 10.2 NaN and comparisons

`NaN` means Not a Number. It behaves oddly:

- `typeof NaN === "number"`
- `NaN === NaN` is `false`
- Any comparison with `NaN` (`<`, `>`, `==`, `===`) is `false`

Use `Number.isNaN()` (ES6) to test strictly for NaN:

```js
Number.isNaN(NaN); // true
Number.isNaN("str" - 12); // true
Number.isNaN("24"); // false
```

Polyfill for older environments:

```js
Number.isNaN =
  Number.isNaN ||
  function (v) {
    return v !== v;
  };
```

`Object.is()` (ES6) implements SameValue: `Object.is(NaN, NaN)` is `true`, and `Object.is(+0, -0)` is `false`.

## 10.3 Short-circuiting with `&&` and `||`

- `x && y`: evaluates `y` only if `x` is truthy. Useful to prevent errors and conditionally call functions.
- `x || y`: evaluates `y` only if `x` is falsy. Good for defaults.

Examples:

```js
function T() {
  console.log("T");
  return true;
}
function F() {
  console.log("F");
  return false;
}

T() && F(); // prints T then F
F() && T(); // prints F only
T() || F(); // prints T only
F() || T(); // prints F then T
```

Use pattern to guard property access:

```js
if (obj !== undefined && obj.property) { ... } // safe
// or for optional callback
cb && cb(); // calls only if cb is truthy
```

Be mindful: `0`, `""`, and `false` are valid values but are falsy. Using `||` for defaults may clobber them.

## 10.4 null vs undefined

- `null == undefined` → `true`
- `null === undefined` → `false`

Semantics:

- `undefined` means absence of value or uninitialized.
- `null` is an explicit placeholder intentionally set.

Do not assign `undefined` yourself. Use `null` for intentional emptiness and `typeof` checks for existence to avoid reference errors:

```js
if (typeof foo === "undefined") { ... }
```

## 10.5 Abstract Equality Algorithm (summary)

When `x == y`:

1. If same Type → use `===`.
2. `null` and `undefined` are equal.
3. If one is a Number and the other is a String → convert String to Number.
4. If Boolean is involved → convert Boolean to Number.
5. If Object vs primitive (String/Number/Symbol) → ToPrimitive(object) then repeat.
6. Otherwise false.

This explains conversions like `0 == ''` and `false == '0'`.

## 10.6 Logic operators with Booleans and non-boolean values

Boolean operators return the actual operand value, not strictly `true`/`false`.

`||` returns first truthy value or last value if none:

```js
"hello" || ""; // "hello"
"" || []; // []
0 || {}; // {}
0 || "" || 5; // 5
```

`&&` returns the first falsy value or the last value if all truthy:

```js
"hello" && ""; // ""
1 && 5; // 5
0 && {}; // 0
```

Use these behaviours intentionally, but remember falsy values that might be legitimate (0, '', false).

## 10.7 Automatic type conversions (gotchas)

- `+` with a string concatenates: `5 + "7" === "57"`.
- `-`, `*`, `/` coerce to numbers: `"5" - 2 === 3`.
- Non-numeric string math → `NaN`: `"a" - "b" // NaN`.
- When you rely on numeric math, convert explicitly with `Number()` or `parseInt/parseFloat`.

## 10.8 Empty array and coercion oddity

`[] == false` is `true`.

Why: `[]` → `""` when ToPrimitive, `""` → `0` when ToNumber, then `0 == false` → `true`.

But `[]` is truthy in boolean contexts:

```js
[] ? "truthy" : "falsy"; // "truthy"
```

So remember: `==` combines shape conversions that can surprise you.

## 10.9 Equality comparison variants - quick reference

- **SameValue** (use `Object.is`): strictest; `Object.is(NaN, NaN)` is `true`, `Object.is(+0, -0)` is `false`.
- **SameValueZero** (used by `Array.prototype.includes`): like SameValue but `+0` and `-0` are treated as equal.
- **Strict equality** (`===`): no type conversion; `+0 === -0` true; `NaN === NaN` false.
- **Abstract equality** (`==`): type conversions applied per spec.

Prefer `===` for comparisons unless you intentionally want coercion and handle it explicitly.

## 10.10 Relational operators (`<`, `<=`, `>`, `>=`)

- If both operands are strings → lexicographic comparison (character code order).

  - `'100' > '12'` is `false` (lexicographic).

- If one is a string and the other number → convert the string to a number, then compare.

  - `'3' > 2` → `true`.

- Non-numeric string converts to `NaN` → relational comparisons with `NaN` are `false`.
- `null` converts to `0` when compared with a number: `1 > null` → `true`.
- `undefined` converts to `NaN` in numeric contexts, so comparisons involving `undefined` are usually `false`.

Use explicit conversion and be careful with mixed-type relational comparisons.

## 10.11 Inequality operators (`!=`, `!==`)

- `!=` is the inverse of `==` (with coercion).
- `!==` is the inverse of `===` (strict, no coercion).

Prefer `!==` to avoid coercion surprises.

## 10.12 Grouping Boolean expressions

Use parentheses to make complex Boolean logic readable and correct:

```js
if ((age >= 18 && height >= 5.11) || (status === "royalty" && hasInvitation)) {
  // allowed
}
```

Consider assigning intermediate boolean variables to make intent explicit.

## 10.13 Bitfields (compact multi-state flags)

A bitfield packs boolean flags into a number (up to 32 bits). Useful for fast checks and compact state.

```js
const KEY_U = 1; // 0001
const KEY_D = 2; // 0010
const KEY_L = 4; // 0100
const KEY_R = 8; // 1000

// set flags
bitfield |= KEY_U; // turn on Up
// clear flag
bitfield &= ~KEY_U; // turn off Up
// check exact match
if ((bitfield & (KEY_U | KEY_L)) === (KEY_U | KEY_L)) {
  /* Up and Left */
}
// check presence
if (bitfield & KEY_U) {
  /* Up is pressed */
}
```

Bitfields are compact and fast, but less readable. Use constants and helper functions for maintainability.

## 10.14 Practical helper functions

```js
// safe equality for instants (no coercion)
const eqStrict = (a, b) => a === b;

// robust NaN-aware equality like SameValue
const sameValue = (x, y) =>
  Object.is
    ? Object.is(x, y)
    : x === y
    ? x !== 0 || 1 / x === 1 / y
    : x !== x && y !== y;

// safe numeric compare
const numEq = (a, b) => Number(a) === Number(b);

// check valid Date
const isValidDate = (d) => d instanceof Date && !Number.isNaN(d.getTime());
```

## 10.15 Practical rules — TL;DR

- Use `===` and `!==` unless you intentionally want coercion.
- When comparing numbers or doing math, coerce explicitly with `Number()` or `parse*`.
- To detect `NaN`, use `Number.isNaN()` or `value !== value`.
- Watch out for falsy-but-valid values: `0`, `''`, `false`.
- Use `Object.is()` if you need NaN equality or to distinguish +0 and -0.
- Use bitfields for compact multi-flag handling, but wrap operations in named constants and helpers.

# Chapter 11. Conditions

Practical, compact guide to conditionals in JavaScript: ternaries, `if/else`, `switch`, short-circuiting, common pitfalls, and a cleaner alternative (strategy pattern).

## 11.1 Ternary operator (`? :`)

A concise single-expression `if/else`. Useful for returning a value or inline assignment.

```js
const animal = "kitty";
const result = animal === "kitty" ? "cute" : "still nice";
```

- Ternary is an expression — it **returns** a value and can be assigned.
- The else branch is mandatory (syntax requires it). If you only need side effects, use a normal `if`.
- You **cannot** use control statements like `break` or `return` inside the two branches directly (they are statements). You can return the entire ternary:

```js
return animal === "kitty" ? "meow" : "woof";
```

- Comma operator can be used in branches but hurts readability:

```js
let a = 0,
  str = "not a";
let b = a === 0 ? ((a = 1), (str += " test")) : (a = 2);
// b === 'not a test'
```

- Nested ternaries are legal but degrade readability. Prefer parentheses and short expressions if you must:

```js
const v = foo ? (bar ? 1 : 2) : 3;
```

If it gets complex, switch to `if/else` or refactor into functions.

## 11.2 `switch` statement

`switch` tests an expression against case values and executes the matching block.

```js
switch (value) {
  case 1:
    console.log("I will run if value === 1");
    break;
  case 2:
    console.log("I will run if value === 2");
    break;
  default:
    console.log("no match");
}
```

- **`break` matters** — without `break` execution falls through to the next case. Useful intentionally for shared behavior:

```js
switch (x) {
  case "a":
  case "b":
  case "c":
    console.log("a, b, or c");
    break;
  case "d":
    console.log("only d");
    break;
}
```

- Case expressions may be any expression (function calls, concatenation, etc.). They are compared with `===` semantics (no coercion).
- Use `default` for fallback logic.

## 11.3 `if / else if / else`

Basic conditional flow:

```js
if (i < 1) {
  console.log("i is smaller than 1");
} else if (i < 2) {
  console.log("i is smaller than 2");
} else {
  console.log("none matched");
}
```

Key notes:

- Only the first true branch executes — subsequent `else if`s are skipped.
- Curly braces are optional for single statements but **always use braces** for multi-statement blocks to avoid bugs:

```js
if (i < 1) console.log("i < 1");
console.log("this runs regardless"); // likely a bug if you intended it to be conditional
```

- Conditions are coerced to booleans (truthy / falsy). Use `===` / `!==` when you need type-safe comparisons.

---

## 11.4 Strategy pattern (object dispatch) — nicer alternative to big `switch`

When you have many cases or dynamic keys, use an object mapping to functions. It's easier to test and extend.

```js
const AnimalSays = {
  dog() {
    return "woof";
  },
  cat() {
    return "meow";
  },
  lion() {
    return "roar";
  },
  default() {
    return "moo";
  },
};

function makeAnimalSpeak(animal) {
  const speak = AnimalSays[animal] || AnimalSays.default;
  console.log(`${animal} says ${speak()}`);
}
```

- Benefits: scalable, testable, no fall-through bugs, easy to extend at runtime.
- Add validation or use `hasOwnProperty` if you worry about prototype pollution.

## 11.5 Short-circuiting with `||` and `&&`

Use these to guard expressions, provide defaults, or conditionally execute:

### `||` — first truthy or last value

```js
const obj = nullableObj || {}; // fallback if nullableObj is falsy
const val = 0 || 5; // 5 (0 is falsy)
```

### `&&` — first falsy or last value

```js
x === 10 && alert("x is 10"); // alerts only if condition true
cb && cb(); // call cb only if it is truthy (exists)
```

Cautions:

- `0`, `''`, and `false` are valid values but falsy: `val = param || default` will replace legitimate `0` or `''`. Use explicit checks or ES6 default parameters when appropriate:

```js
function f(x = 10) { ... } // safer for function defaults
```

- Order matters: use the guard first to avoid runtime errors:

```js
if (obj && obj.prop) { ... } // safe
// NOT: if (obj.prop && obj) — may throw if obj is undefined
```

## 11.6 Boolean expressions and grouping

- Parentheses clarify precedence and intent. Use them liberally in complex conditions:

```js
if ((age >= 18 && height >= 5.11) || (status === "royalty" && hasInvitation)) {
  // ...
}
```

- Breaking complex logic into well-named boolean variables improves readability:

```js
const isLegal = age >= 18;
const isTall = height >= 5.11;
if ((isLegal && isTall) || (isRoyalty && hasInvitation)) { ... }
```

## 11.7 Common pitfalls & best practices

- **Prefer `===` / `!==`** to avoid implicit coercion surprises.
- **Avoid complex nested ternaries**; they are hard to read and maintain.
- **Always use `break`** in `switch` cases unless intentional fall-through — comment fall-through cases for clarity.
- **Guard property access** (`obj && obj.prop`) or use optional chaining (`obj?.prop`) if your environment supports it.
- **Do not use `||` for defaults** if `0`, `false`, or `''` are valid inputs — use ES6 default params or explicit `null`/`undefined` checks.
- **Don’t shadow `undefined`** or assign to it. Use `void 0` for a guaranteed undefined if you need it.
- **Prefer declarative dispatch (strategy, map)** for many conditions rather than long `if/else` or `switch` blocks.
- **Test edge cases**: falsy values, unexpected types, and short-circuit side effects.

### Quick examples

Ternary vs if/else

```js
const score = 85;
const grade = score >= 90 ? "A" : score >= 80 ? "B" : "C"; // readable if short
// or
if (score >= 90) grade = "A";
else if (score >= 80) grade = "B";
else grade = "C";
```

Guarding:

```js
// safe
if (arr && arr.length) {
  /* use arr[0] */
}

// optional chaining (modern)
if (arr?.length) {
  /* use arr[0] */
}
```

Strategy example (dynamic):

```js
const actions = { add: () => 1, sub: () => -1 };
function act(op) {
  (actions[op] || (() => 0))();
}
```

# Chapter 12. Arrays

Comprehensive, practical reference for arrays - creation, conversion, iteration, transformation, mutation, and common utilities. Examples use modern idiomatic JavaScript and show backward-compatible alternatives where relevant.

## 12.1 Array-like objects → Arrays

**Array-like objects** have numeric keys and a `length` property (examples: `arguments`, `NodeList`, `HTMLCollection`). They do not inherit `Array.prototype`.

Convert to a real array:

- ES6+

```js
Array.from(arrayLike);
[...arrayLike];
Object.values(arrayLike); // when keys are 0..n-1
```

- ES5 (and older)

```js
Array.prototype.slice.call(arrayLike); // or [].slice.call(arrayLike)
```

Call array methods directly on array-like objects:

```js
Array.prototype.forEach.call(domList, fn);
[].forEach.bind(arrayLike)(fn);
```

`Array.from` accepts a map function:

```js
Array.from(domList, (el) => el.tagName);
```

## 12.2 Reducing values (`Array.prototype.reduce`)

`reduce` collapses an array into a single value.

Sum:

```js
[1, 2, 3, 4].reduce((a, b) => a + b, 0); // 10
```

Flatten array of objects to an object:

```js
// ES5
array.reduce(function (obj, cur) {
  obj[cur.key] = cur.value;
  return obj;
}, {});

// ES6
array.reduce((obj, cur) => Object.assign(obj, { [cur.key]: cur.value }), {});
// or with spread (beware performance)
array.reduce((o, c) => ({ ...o, [c.key]: c.value }), {});
```

Map using reduce (illustrative - prefer `map`):

```js
function map(list, fn) {
  return list.reduce((acc, item) => acc.concat(fn(item)), []);
}
```

Find min/max:

```js
arr.reduce((a, b) => Math.min(a, b), Infinity);
```

Unique values:

```js
arr.reduce((prev, n) => {
  if (prev.indexOf(n) === -1) prev.push(n);
  return prev;
}, []);
```

## 12.3 Mapping values (`map`)

Create a new array from an existing one.

```js
["one", "two", "three"].map((s) => s.length); // [3,3,5]
```

Callback receives `value, index, array`. Optional second argument sets `this`.

## 12.4 Filtering (`filter`)

Return elements that pass a predicate.

```js
[5, 32, 43, 4].filter((n) => n % 2 !== 0); // [5,43]

people.filter((p) => p.age < 35);
```

Quick remove falsy values:

```js
[0, undefined, {}, null, "", true, 5].filter(Boolean); // [{}, true, 5]
```

## 12.5 Sorting (`sort`)

`sort()` mutates array. Default sorts as strings - often surprising.

Numeric ascending:

```js
[100, 1000, 10, 1].sort((a, b) => a - b);
```

String locale order:

```js
arr.sort((a, b) => a.toString().localeCompare(b));
```

Sort by length:

```js
words.sort((a, b) => b.length - a.length); // longest first
```

Sort dates or anything numeric by difference:

```js
dates.sort((a, b) => b - a); // descending
```

Sort even/odd and then value:

```js
arr.sort((a, b) => (a & 1) - (b & 1) || a - b);
```

## 12.6 Iteration patterns

- Traditional for:

```js
for (let i = 0; i < arr.length; i++) { ... }
```

- Reverse loop:

```js
for (let i = arr.length - 1; i >= 0; i--) { ... }
```

- `for...in` - iterates enumerable property keys - avoid for arrays (includes inherited keys).

- `for...of` - iterate values (ES6):

```js
for (const v of myArray) { ... }
```

- `Array.prototype.forEach`:

```js
arr.forEach((v,i) => { ... });
```

Note: cannot `break` out of `forEach`.

- `every` stops when predicate returns false - useful for partial iteration.
- `some` stops when predicate returns true - useful for partial iteration.

## 12.7 Destructuring arrays (ES6)

```js
const [len, height, hyp] = [3, 4, 5];
const [, b, , c] = [1, 2, 3, 4]; // b=2, c=4
const [a, b, ...rest] = [1, 2, 3, 4]; // rest = [3,4]
function area([l, h]) {
  return (l * h) / 2;
}
```

## 12.8 Removing duplicates

- Using `filter`:

```js
arr.filter((v, i, self) => self.indexOf(v) === i);
```

- Using `Set` (ES6):

```js
[...new Set(arr)];
```

## 12.9 Comparing arrays

Simple shallow compare:

```js
JSON.stringify(a) === JSON.stringify(b); // works for JSON-serializable, non-cyclic
```

Deep recursive compare (handle cycles with care) - example provided earlier; be cautious of cycles.

## 12.10 Reversing arrays

In-place:

```js
[1, 2, 3].reverse(); // [3,2,1] - mutates original
```

Deep reverse - recursive for nested arrays (mutates).

## 12.11 Shallow clone

Shallow copy of an array:

```js
arr.slice();
Array.from(arr);
[...arr];
```

## 12.12 Concatenation

- `concat` returns new array:

```js
arr1.concat(arr2, "c", "d");
```

- Spread:

```js
[...arr1, ...arr2, "c", "d"];
```

- Append without copying first array:

```js
longArray.push(...shortArray); // ES6
// or longArray.push.apply(longArray, shortArray); // caution for very large arrays
```

## 12.13 Merge two arrays as key-value object

```js
const columns = ["Date", "Number", "Size"];
const rows = ["2001", "5", "Big"];
const result = rows.reduce((res, field, i) => {
  res[columns[i]] = field;
  return res;
}, {});
```

## 12.14 Spread / Rest

- Spread in arrays:

```js
[1, 2, 3, ...[4, 5, 6]];
Math.max(...nums);
```

- Rest in destructuring / function args:

```js
const [x, y, ...rest] = [1, 2, 3, 4];
function fn(a, b, ...rest) {}
```

## 12.15 Filtering examples

Filter by predicate:

```js
[1, 2, 3, 4, 5].filter((v) => v > 2); // [3,4,5]
```

Filter words starting with letter:

```js
words.filter((w) => w && w[0].toLowerCase() === "a");
```

## 12.16 Searching arrays

- Find element:

```js
people.find((p) => p.name === "bob");
```

- Find index:

```js
arr.findIndex((x) => x.value === 3); // -1 if not found
```

## 12.17 String ↔ Array

- Split into array:

```js
"StackOverflow".split(""); // characters
[..."string"]; // spread - preserves Unicode code points better for many cases
```

## 12.18 Removing items

- Remove first:

```js
arr.shift(); // returns removed element, mutates
```

- Remove last:

```js
arr.pop();
```

- Splice remove/insert:

```js
arr.splice(index, count, ...items); // returns removed items
```

- `delete arr[index]` leaves hole - use only when you want to keep length and create undefined at index.

- Resize:

```js
arr.length = 2; // truncates or extends with undefined
```

## 12.19 Clearing arrays

- Reassign (new reference):

```js
arr = [];
```

- Clear in-place (preserve references - preferred when others hold reference):

```js
arr.length = 0;
```

- `arr.splice(0)` returns removed items - less efficient.

## 12.20 Min / Max

- Using apply (older):

```js
Math.min.apply(null, arr);
```

- Using spread (ES6):

```js
Math.min(...arr);
```

- Using reduce:

```js
arr.reduce((a, b) => Math.min(a, b), Infinity);
```

## 12.21 Initialization options

- Literal:

```js
[1, 2, 3];
```

- `new Array(n)` creates array of length `n` with holes - be careful.
- `Array.of(23)` creates `[23]` (unlike `Array(23)`).
- `Array.from({length:5}, (_,i)=>i*i)` builds arrays programmatically.

## 12.22 Join to string

```js
[1, 800, 555, 1234].join("-"); // "1-800-555-1234"
```

## 12.23 Splice for add/remove

Remove first occurrence of value:

```js
const i = values.indexOf(3);
if (i >= 0) values.splice(i, 1);
```

Insert at index:

```js
arr.splice(index, 0, item);
```

## 12.24 `entries()` (ES6)

Iterate index/value pairs:

```js
for (const [i, el] of arr.entries()) {
  console.log(i, el);
}
```

## 12.25 Remove by value - copy or mutate

Copy without value:

```js
const filtered = arr.filter((v) => v !== toRemove);
```

Mutate and remove all occurrences:

```js
let index;
while ((index = arr.indexOf(toRemove)) !== -1) {
  arr.splice(index, 1);
}
```

Remove first:

```js
const idx = arr.indexOf(toRemove);
if (idx !== -1) arr.splice(idx, 1);
```

## 12.26 Flattening arrays

- Shallow flatten (one level):

```js
[].concat(...arr); // ES6 spread
// or
[].concat.apply([], arr); // ES5
```

- Deep flatten for numbers using `toString` hack - only works for arrays of numbers:

```js
deeplyNested.toString().split(",").map(Number);
```

For general objects and nested heterogeneous arrays, use a recursive flatten or `arr.flat(depth)` (ES2019).

## 12.27 Append / Prepend

- Prepend:

```js
arr.unshift(1, 2); // returns new length
```

- Append:

```js
arr.push(4, 5);
```

## 12.28 Object keys/values → array of pairs

```js
const obj = { k1: 10, k2: 3 };
const arr = Object.keys(obj).map((k) => [k, obj[k]]);
// or (ES2017)
Object.entries(obj); // [['k1',10], ['k2',3]]
```

## 12.29 Logical connectives - `.some` and `.every`

- `.some(fn)` returns true if any element satisfies predicate (OR).
- `.every(fn)` returns true if all elements satisfy predicate (AND).

Examples:

```js
[2, 4, 7, 9].some((x) => x % 2 !== 0); // true
[1, 1, 1].every((x, i, arr) => x === arr[0]); // true
```

## 12.30 Check array identity

- Detect array:

```js
Array.isArray(obj);
```

- `instanceof Array` works but can fail if prototype changed or across frames.

## 12.31 Insert helper (example)

Insert at index:

```js
arr.splice(index, 0, item);
```

Optional `insert` extension (mutating) - avoid modifying prototypes in production.

## 12.32 Sort multidimensional arrays

Sort by second column:

```js
array.sort((a, b) => a[1] - b[1]);
```

## 12.33 Test all array items for equality

```js
arr.every((item, i, list) => item === list[0]);
```

For objects, compare a property:

```js
data.every((item, i, list) => item.name === list[0].name);
```

## 12.34 Copy part of array (`slice`)

Shallow copy a range:

```js
arr.slice(begin, end); // end excluded
arr.slice(0, 2); // first two elements
arr.slice(4); // from index 4 to end
```

# Chapter 13. Objects

JavaScript objects are dynamic collections of properties. Each property has a **descriptor** that defines its behavior.

### Property descriptor fields

| Field          | Meaning                                                |
| -------------- | ------------------------------------------------------ |
| `value`        | Stored value (data property).                          |
| `writable`     | Whether you can reassign the value.                    |
| `enumerable`   | Whether it appears in `for...in` or `Object.keys`.     |
| `configurable` | Whether descriptor can be changed or property deleted. |
| `get`          | Getter function (replaces `value`).                    |
| `set`          | Setter function (replaces `value`).                    |

A property is **either** a data property (`value`, `writable`) **or** an accessor property (`get`, `set`). Never both.

## 13.1 Shallow cloning

### ES6+

```js
const existing = { a: 1, b: 2 };
const clone = Object.assign({}, existing);
```

Using object spread:

```js
const { ...clone } = existing;
```

### ES5 fallback

```js
var clone = {};
for (var key in existing) {
  if (existing.hasOwnProperty(key)) clone[key] = existing[key];
}
```

Shallow means nested objects are still the same reference.

## 13.2 Object.freeze

Prevents:

- adding properties
- removing properties
- modifying descriptors
- changing existing values

Does **not** deep-freeze child objects.

```js
const obj = {
  foo: "foo",
  bar: [1, 2, 3],
  nested: { x: 1 },
};
Object.freeze(obj);

obj.newProp = true; // ignored
obj.foo = "nope"; // ignored
delete obj.foo; // ignored

obj.bar.push(4); // allowed (bar is not frozen)
obj.nested.x = 99; // allowed
```

Strict mode throws instead of silently failing.

## 13.3 Deep cloning

No built-in deep clone. Use:

### For simple JSON-safe objects:

```js
const copy = JSON.parse(JSON.stringify(obj));
```

Breaks:

- functions
- Dates → become strings
- undefined and symbols
- cyclic objects

### Manual deep clone example (handles arrays, objects, dates, detects cycles):

Provided in original text; core idea:

```js
function deepClone(obj, seen = []) {
  if (obj === null || typeof obj !== "object") return obj;
  if (seen.includes(obj)) throw new Error("Circular");

  seen.push(obj);

  if (obj instanceof Date) return new Date(obj.getTime());
  if (Array.isArray(obj)) return obj.map((x) => deepClone(x, seen));

  const result = {};
  for (const key in obj) {
    if (obj.hasOwnProperty(key)) result[key] = deepClone(obj[key], seen);
  }
  return result;
}
```

## 13.4 Iterating over properties

### Old-school and dangerous:

```js
for (const key in obj) {
  if (obj.hasOwnProperty(key)) console.log(key);
}
```

### Better:

```js
Object.keys(obj); // enumerable own keys
Object.getOwnPropertyNames(obj); // all own keys including non-enumerable
Object.entries(obj); // [key, value] pairs
Object.values(obj); // values
```

## 13.5 Object.assign

Copies enumerable own properties from sources into target:

```js
const user = { first: "John" };
Object.assign(user, { last: "Doe", age: 39 });
```

Shallow cloning:

```js
const clone = Object.assign({}, user);
```

Merge multiple:

```js
Object.assign(obj1, obj2, obj3);
```

Primitives: strings contribute indexed character properties; `null` and `undefined` ignored.

## 13.6 Object spread/rest

Syntactic sugar for shallow merges:

```js
const obj = { a: 1 };
const merged = { ...obj, b: 2 };
```

Equivalent to:

```js
Object.assign({}, obj, { b: 2 });
```

Shallow, not deep.

## 13.7 Object.defineProperty

Define property with explicit descriptor:

```js
const obj = {};
Object.defineProperty(obj, "foo", {
  value: "bar",
  writable: true,
  configurable: true,
  enumerable: true,
});
```

Multiple:

```js
Object.defineProperties(obj, {
  a: { value: 1 },
  b: { value: 2, writable: false },
});
```

## 13.8 Accessor properties (getters/setters)

```js
const person = { name: "John", surname: "Doe" };

Object.defineProperty(person, "fullName", {
  get() {
    return this.name + " " + this.surname;
  },
  set(value) {
    [this.name, this.surname] = value.split(" ");
  },
});
```

Cannot mix `value/writable` with `get/set`.

## 13.9 Dynamic property names

Use bracket notation:

```js
dictionary[word];
obj[propertyName] = 1;
```

Computed keys in object literal:

```js
const key = "test";
const obj = { [key]: 1 };
```

## 13.10 Arrays are Objects

Arrays are objects with:

- numeric keys
- a `length` property
- `Array.prototype` as prototype

Array-like objects (like NodeList) mimic arrays but lack array methods.

Use:

```js
Array.from(nodeList);
```

## 13.11 Object.seal

Prevents adding or removing properties, but allows modifying values.

```js
const obj = { foo: "foo" };
Object.seal(obj);

obj.foo = "new"; // allowed
obj.newProp = 1; // ignored or TypeError in strict mode
delete obj.foo; // ignored
```

## 13.12 Convert values to array

```js
const values = Object.keys(obj).map((k) => obj[k]);
// Or simply:
Object.values(obj); // ES8+
```

## 13.13 Retrieving properties

Summary:

| Method                       | Own?    | Enumerable? | Prototype? |
| ---------------------------- | ------- | ----------- | ---------- |
| `for...in`                   | ✔       | ✔           | ✔          |
| `Object.keys`                | ✔       | ✔           | ✖          |
| `Object.getOwnPropertyNames` | ✔       | ✔ + ✖       | ✖          |
| custom recursion             | depends | depends     | ✔          |

## 13.14 Read-only property

```js
Object.defineProperty(obj, "foo", {
  value: "original",
  writable: false,
});
```

Assignments silently fail.

## 13.15 Non-enumerable properties

```js
Object.defineProperty(obj, "secret", {
  value: 123,
  enumerable: false,
});
```

Won’t show in:

- `for...in`
- `Object.keys`

## 13.16 Lock property descriptor (`configurable: false`)

Prevents:

- changing descriptor
- converting between data and accessor
- deletion

```js
Object.defineProperty(obj, "foo", {
  value: "x",
  configurable: false,
});
```

## 13.17 Object.getOwnPropertyDescriptor

```js
Object.getOwnPropertyDescriptor(obj, "hello");
```

Shows full descriptor.

## 13.18 Summary of descriptor behavior

- Data property: `{ value, writable }`
- Accessor: `{ get, set }`
- Shared: `{ enumerable, configurable }`

Default descriptor for literal object properties:

```js
{ value: X, writable: true, enumerable: true, configurable: true }
```

## 13.19 Object.keys

```js
Object.keys(obj); // ['a','b','c']
```

Enumerates enumerable own properties.

## 13.20 Special property names

Use bracket syntax for:

- spaces
- unicode
- numeric property names
- reserved words

```js
obj["weird key"] = 1;
obj[123] = 2;
```

## 13.21 Creating iterable objects

Implement `[Symbol.iterator]`:

```js
const iterable = {
  [Symbol.iterator]() {
    let done = false;
    return {
      next() {
        if (!done) {
          done = true;
          return { done: false, value: "One" };
        }
        return { done: true };
      },
    };
  },
};

for (const x of iterable) console.log(x);
```

## 13.22 Object.entries

ES8:

```js
Object.entries(obj);
// [['one',1], ['two',2]]
```

Useful for destructuring iteration:

```js
for (const [k,v] of Object.entries(obj)) { ... }
```

## 13.23 Object.values

ES8:

```js
Object.values({ 0: "a", 1: "b" });
// ['a','b']
```

Equivalent order to `for...in` for enumerable own properties.

# Chapter 14 . Arithmetic (Math)

## 14.1 Constants (quick reference)

- `Math.E` ≈ 2.718281828 (base of natural logarithm)
- `Math.LN10` ≈ 2.302585092 (ln(10))
- `Math.LN2` ≈ 0.693147180 (ln(2))
- `Math.LOG10E` ≈ 0.434294482 (log₁₀e)
- `Math.LOG2E` ≈ 1.442695041 (log₂e)
- `Math.PI` ≈ 3.141592653589793
- `Math.SQRT1_2` ≈ 0.707106781 (√(1/2))
- `Math.SQRT2` ≈ 1.414213562 (√2)

Number constants:

- `Number.EPSILON` ≈ 2.220446049250313e-16 (difference between 1 and the next representable number)
- `Number.MAX_SAFE_INTEGER` = 2^53 - 1
- `Number.MIN_SAFE_INTEGER` = -(2^53 - 1)
- `Number.MAX_VALUE` ≈ 1.7976931348623157e308
- `Number.MIN_VALUE` ≈ 5e-324
- `Infinity` / `-Infinity` represent ±∞.

## 14.2 Remainder / Modulus (`%`)

- `a % b` returns the remainder after integer division. Sign follows the dividend (first operand):

```js
(42 % 10) - // 2
  (42 % 10); // -2
(42 % -10) - // 2
  (42 % -10); // -2
```

Common uses:

- even check: `x % 2 === 0`
- cyclic indexes: `i = (i + d + n) % n` ensures result in `[0, n)`
- fractional part: `fraction = x % 1` (note: sign preserved for negatives)

## 14.3 Rounding

- `Math.round(x)` — nearest integer, ties round _up_ (toward +∞): `Math.round(2.5) === 3`, `Math.round(-2.5) === -2`.
- `Math.ceil(x)` — round up (toward +∞): `Math.ceil(2.3) === 3`, `Math.ceil(-1.1) === -1`.
- `Math.floor(x)` — round down (toward -∞): `Math.floor(2.7) === 2`, `Math.floor(-1.1) === -2`.
- `Math.trunc(x)` (ES6) — remove fractional part (toward 0): `Math.trunc(2.7) === 2`, `Math.trunc(-2.7) === -2`.

Round to `places`:

```js
function roundTo(value, places) {
  const p = Math.pow(10, places);
  return Math.round(value * p) / p;
}
```

Variants: `ceilTo` / `floorTo` replace `Math.round` with `Math.ceil` / `Math.floor`.

## 14.4 Trigonometry (radians)

All core trig functions expect radians. Convert: `deg * Math.PI / 180`.

- `Math.sin(x)`, `Math.cos(x)`, `Math.tan(x)`
- Inverses: `Math.asin`, `Math.acos`, `Math.atan`
- `Math.atan2(y, x)` — correct usage: first argument **y**, second **x**; returns angle in `(-π, π]`. Example: direction from p1 to p2:

```js
Math.atan2(p2.y - p1.y, p2.x - p1.x);
```

- Hyperbolic variants: `Math.sinh`, `Math.cosh`, `Math.tanh`, and `Math.asinh`, `Math.acosh`, `Math.atanh`.

## 14.5 Bitwise operators

All operate on 32-bit integers (`ToInt32` conversion).

- OR `|`, AND `&`, XOR `^`, NOT `~`
- Shifts: `<<` (left), `>>` (signed right, sign-propagating), `>>>` (unsigned right, zero-fill)
- Assignment forms: `a |= b`, `a &= b`, etc.

Notes:

- `a << n` ≈ `Math.floor(a) * 2^n` for integers.
- `>>>` always yields a non-negative number. For negative inputs `>>>` produces an unsigned interpretation (large positive).
- Bitwise ops are restricted to 32-bit; using them coerces numbers to signed 32-bit integers.

Endian caution when manipulating typed arrays and raw bytes — test platform endianness before low-level bit hacks.

## 14.6 Increment / 14.25 Decrement (`++`, `--`)

- Prefix (`++x`) increments and returns new value.
- Postfix (`x++`) returns old value, then increments.
  Prefer prefix in hot loops (avoids temporary in some engines), but it's a micro-optimization.

Example:

```js
let a = 5;
let b = a++; // b=5, a=6
let c = ++a; // a=7, c=7
```

`++` and `--` **mutate** the variable; not allowed on constants/literals.

## 14.7 Exponentiation

- `Math.pow(a, b)` — standard.
- `a ** b` — exponent operator (ES2016+).
- nth root: `Math.pow(value, 1 / n)`.

## 14.8 Random floats & integers

- `Math.random()` → float in `[0, 1)`.
  Helpers:

```js
// [min, max)
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
// [min, max) integers
function getRandomInt(min, max) {
  return Math.floor(Math.random() * (max - min)) + min;
}
// [min, max] inclusive integers
function getRandomIntInclusive(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}
```

Random between min and max shorthand:

```js
function randomBetween(min, max) {
  return Math.floor(Math.random() * (max - min + 1) + min);
}
```

## 14.9 Addition (`+`)

- Numeric addition or string concatenation. If either operand is a string, result is string.
- Coercion: `true` → `1` when numeric; `null` → `0`; `undefined + number` → `NaN`.
  Be explicit: `Number(...)` or `String(...)` when mixing types.

## 14.10 Endianness & typed arrays (brief)

Detect little-endian:

```js
function isLittleEndian() {
  const buf = new ArrayBuffer(4);
  new Uint32Array(buf)[0] = 0x0f000000;
  return new Uint8Array(buf)[0] !== 0x0f;
}
```

When mapping pixels to `Uint32Array` you must adapt masks depending on endianness.

## 14.11 Weighted randomness / simulate events

Weighted pick:

```js
function weightedIndex(weights) {
  const sum = weights.reduce((s, w) => s + w, 0);
  const r = Math.random() * sum;
  let acc = 0;
  for (let i = 0; i < weights.length; i++) {
    acc += weights[i];
    if (r < acc) return i;
  }
  return -1;
}
```

## 14.12 Subtraction (`-`), 14.14 Multiplication (`*`), 14.24 Division (`/`)

Standard arithmetic. Non-numeric strings coerce to `NaN` for numeric ops (`"5" - 1 === 4`, `"foo" - 1 === NaN`).

## 14.13 Max & Min

- `Math.max(...arr)`, `Math.min(...arr)` (ES6 spread).
- Older: `Math.max.apply(null, arr)`.

## 14.14 Clamp a number

```js
function clamp(min, max, val) {
  return Math.min(Math.max(min, +val), max);
}
```

## 14.15 Ceil & Floor (recap)

- `Math.ceil(x)` → smallest integer ≥ x.
- `Math.floor(x)` → largest integer ≤ x.

## 14.16 Roots

- `Math.sqrt(x)` — square root.
- `Math.cbrt(x)` — cube root (ES6).
- `Math.pow(x, 1 / n)` — nth root.

## 14.17 Gaussian-like randomness

Approximate normal-ish distribution by averaging multiple uniform samples:

```js
function randomGaussian(samples = 3) {
  let s = 0;
  for (let i = 0; i < samples; i++) s += Math.random();
  return s / samples;
}
```

More samples → closer to bell curve. For true Gaussian use Box–Muller.

## 14.18 `Math.atan2` direction

Correct usage: `Math.atan2(deltaY, deltaX)` returns an angle in radians between `-π` and `π`.

## 14.19 From polar → Cartesian

Given `dir` (radians) and `dist`:

```js
const x = Math.cos(dir) * dist;
const y = Math.sin(dir) * dist;
```

If your Y axis points up and your coordinate system expects a different convention, swap/negate as needed.

## 14.20 `Math.hypot` (distance)

Pythagoras for N-dimensions:

```js
Math.hypot(dx, dy); // sqrt(dx*dx + dy*dy)
```

## 14.21 Periodic functions with `Math.sin`

Oscillator template:

```js
function oscillator(time, frequency = 1, amplitude = 1, phase = 0, offset = 0) {
  return (
    Math.sin(time * frequency * 2 * Math.PI + phase * 2 * Math.PI) * amplitude +
    offset
  );
}
```

Use for waves, animations, LFOs, etc.

## 14.22 Practical caveats & tips

- Floating point rounding issues are inevitable; use `Number.EPSILON` to compare near-equality.
- Prefer `Math.trunc` over bitwise hacks for truncation when numbers may exceed 32-bit range.
- Bitwise ops coerce to 32-bit signed integers — use with care.
- When performance matters, avoid creating large temporary arrays (e.g., spreading very large arrays into `Math.max(...arr)` can blow the stack).

# Chapter 15. Bitwise operators

Bitwise operators work on the binary representation of numbers. JavaScript converts operands to **signed 32-bit integers** (two’s complement) before applying the operation, and the result is returned as a Number. Because of that conversion, bitwise ops are ideal for 32-bit integer work (flags, masks, fast integer math) but **not** for arbitrary large integers unless you use `BigInt`.

## 15.0 How numbers are prepared (ToInt32 / two’s complement)

- Before a bitwise operation, JavaScript performs a `ToInt32` conversion. This discards (shifts off) any bits beyond 32 bits.
- Negative integers are represented in **two’s complement**: invert all bits (one’s complement) then add 1.
  Example (4-bit two’s complement):

  - `6` → `0110`
  - invert → `1001` (one’s complement)
  - add 1 → `1010` → represents `-6` in two’s complement.

- Leading 1s on the left (sign extension) do not change the two’s complement value: `1010` and `1111111111010` both represent `-6` for a 32-bit view.

## 15.1 Bitwise AND `&`

Return `1` bit where **both** inputs have `1` at that position.

```js
13 & 7; // 5
// 13:  01101
//  7:  00111
//res:  00101  => 5
```

Practical use:

- **Parity / even-odd**: `n & 1` yields `1` for odd, `0` for even.
- **Masking**: `value & mask` clears bits not in `mask`.

## 15.2 Bitwise OR `|`

Return `1` bit where **either** input has `1`.

```js
13 | 7; // 15
// 13: 01101
//  7: 00111
//res: 01111 => 15
```

Practical use:

- Combine flags: `flags |= FLAG_A;`

## 15.3 Bitwise XOR `^` (exclusive OR)

Return `1` where bits differ.

```js
13 ^ 7; // 10
// 13: 01101
//  7: 00111
//res: 01010 => 10
```

Practical use:

- Toggle bits: `flags ^= FLAG_A;`
- Classic trick: swap two integers without temporary variable (works only for integers):

```js
let a = 11,
  b = 22;
a = a ^ b;
b = a ^ b; // b = original a
a = a ^ b; // a = original b
```

(Readable alternative: use a temp variable — modern engines optimize.)

## 15.4 Bitwise NOT `~`

Flip all bits (one’s complement). Because of two’s complement representation this behaves like `~x === -x - 1`.

```js
~13; // -14
// 13:  0000...01101
// ~13: 1111...10010 => -14 (two's complement)
```

## 15.5 Left shift `<<`

Shift bits left; low bits shifted in on the right are `0`. Equivalent to multiplication by 2^n for integers (within 32-bit range).

```js
5 << 2; // 20
// 5:   00000101
// <<2: 00010100 => 20
```

Use for fast integer multiply by powers of two.

## 15.6 Sign-propagating right shift `>>`

Shift bits right, filling leftmost bits with the **sign bit** (preserves sign). Equivalent to dividing by 2^n and flooring toward -∞ for integers.

```js
(20 >>
  (2 - // 5
    5)) >>
  3; // -1  (sign bit 1 is replicated)
```

## 15.7 Zero-fill right shift `>>>`

Shift right and fill left bits with zeros. Converts negative numbers into large positive unsigned 32-bit values.

```js
-30 >>> 2; // 1073741816
// -30 as 32-bit: 1111...00011110
// >>>2 -> 001111...11000111 => a large positive number
```

Note: for non-negative numbers `>>` and `>>>` produce the same result.

To coerce a Number to unsigned 32-bit integer: `x >>> 0`.

## 15.8 Common practical patterns

- **Check parity**

```js
if (n & 1) {
  /* odd */
} else {
  /* even */
}
```

- **Set / clear / toggle flags**

```js
flags |= FLAG_A; // set
flags &= ~FLAG_A; // clear
flags ^= FLAG_A; // toggle
```

- **Test a flag**

```js
if (flags & FLAG_A) {
  /* FLAG_A present */
}
```

- **Pack small integers into one 32-bit value** (carefully; watch bit widths and overflow)

```js
let packed = (a & 0xff) | ((b & 0xff) << 8) | ((c & 0xff) << 16);
```

## 15.9 Practical cautions & tips

- **Limited to 32 bits.** Bitwise ops operate on signed 32-bit integers. Values outside that range will be truncated (high bits discarded).
- **Signed result.** The internal result is signed 32-bit; use `>>> 0` to view it as unsigned (0..2^32-1).
- **Floating inputs are coerced.** Non-integer numbers are converted to 32-bit integers via `ToInt32`.
- **Not for big integers.** If you need bitwise operations on integers larger than 32 bits, use `BigInt` bitwise operators (`&`, `|`, `^`, `~`, `<<`, `>>`) with `BigInt` operands. Do not mix `Number` and `BigInt`.
- **Readability vs micro-optimization.** Tricks like XOR-swapping exist but hurt readability. Use them only when there's a clear reason.

# Chapter 16. Constructor Functions (The real rules that matter)

## 16.1 Declaring a constructor function

A **constructor function** is just a normal function that you call with `new`. When you do that:

- JavaScript creates a brand-new empty object.
- It sets that object’s internal prototype to `ConstructorFunction.prototype`.
- Inside the function, `this` refers to that new object.
- If you don’t explicitly return an object, JS returns `this` automatically.

Example:

```js
function Cat(name) {
  this.name = name;
  this.sound = "Meow";
}
```

Using it:

```js
let cat = new Cat("Tom");
cat.sound; // "Meow"
```

If you forget `new`, you’ll pollute the global object or hit an error in strict mode. Don’t forget `new`.

## Prototype inheritance with constructor functions

Every function in JS has a `.prototype` object (except arrow functions).
Objects created by the constructor inherit from that `.prototype`.

```js
Cat.prototype.speak = function () {
  console.log(this.sound);
};

cat.speak(); // "Meow"
```

That method is not copied into each instance; all instances share it via the prototype chain.
This is why you don’t define methods inside the constructor unless you intentionally want duplicate functions per object (wasteful).

## The `.constructor` property

Every object created with a constructor function has a `.constructor` that points back to the function:

```js
cat.constructor === Cat; // true
```

Don’t rely on `.constructor` too heavily. It can be changed or broken if you replace a prototype object:

```js
Cat.prototype = {};
new Cat().constructor === Cat; // false now
```

If you must replace a prototype, you also need to fix `.constructor` manually:

```js
Cat.prototype = { constructor: Cat };
```

## instanceof behavior

`instanceof` checks whether an object’s prototype chain includes `ConstructorFunction.prototype`.

```js
cat instanceof Cat; // true
cat instanceof Object; // also true
```

Important: `instanceof` doesn’t check the constructor property, and it doesn’t check names. The prototype chain determines the result.

## Common mistakes you should avoid

Here are the ones beginners screw up all the time:

1. **Forgetting `new`.**

   ```js
   const x = Cat("Tom"); // WRONG — this.name writes to global
   ```

2. **Putting methods inside the constructor.**
   You end up with duplicated function objects on every instance.

3. **Replacing the prototype without fixing `.constructor`.**

4. **Expecting `instanceof` to behave like Java/C#.**
   It doesn't check types the same way, only the prototype chain.

## Quick comparison: constructor functions vs classes

Constructor functions are the old-school way.
`class` syntax does the same thing with cleaner syntax:

```js
class Cat {
  constructor(name) {
    this.name = name;
    this.sound = "Meow";
  }

  speak() {
    console.log(this.sound);
  }
}
```

Under the hood, this is still prototype-based. It's not more “OOP” than constructors. Just less boilerplate.
